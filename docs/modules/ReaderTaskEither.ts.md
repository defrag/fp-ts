---
title: ReaderTaskEither.ts
nav_order: 68
parent: Modules
---

# ReaderTaskEither overview

Added in v2.0.0

---

<h2 class="text-delta">Table of contents</h2>

- [ReaderTaskEither (interface)](#readertaskeither-interface)
- [URI (type alias)](#uri-type-alias)
- [URI](#uri)
- [alt](#alt)
- [ap](#ap)
- [apFirst](#apfirst)
- [apSecond](#apsecond)
- [ask](#ask)
- [asks](#asks)
- [bimap](#bimap)
- [bracket](#bracket)
- [chain](#chain)
- [chainEitherK](#chaineitherk)
- [chainFirst](#chainfirst)
- [chainIOEitherK](#chainioeitherk)
- [chainTaskEitherK](#chaintaskeitherk)
- [filterOrElse](#filterorelse)
- [flatten](#flatten)
- [fold](#fold)
- [fromEither](#fromeither)
- [fromEitherK](#fromeitherk)
- [fromIOEither](#fromioeither)
- [fromIOEitherK](#fromioeitherk)
- [fromOption](#fromoption)
- [fromPredicate](#frompredicate)
- [fromReaderEither](#fromreadereither)
- [fromTaskEither](#fromtaskeither)
- [fromTaskEitherK](#fromtaskeitherk)
- [getApplyMonoid](#getapplymonoid)
- [getApplySemigroup](#getapplysemigroup)
- [getOrElse](#getorelse)
- [getReaderTaskValidation](#getreadertaskvalidation)
- [getSemigroup](#getsemigroup)
- [left](#left)
- [leftIO](#leftio)
- [leftReader](#leftreader)
- [leftReaderTask](#leftreadertask)
- [leftTask](#lefttask)
- [local](#local)
- [map](#map)
- [mapLeft](#mapleft)
- [orElse](#orelse)
- [readerTaskEither](#readertaskeither)
- [readerTaskEitherSeq](#readertaskeitherseq)
- [right](#right)
- [rightIO](#rightio)
- [rightReader](#rightreader)
- [rightReaderTask](#rightreadertask)
- [rightTask](#righttask)
- [run](#run)
- [swap](#swap)

---

# ReaderTaskEither (interface)

**Signature**

```ts
export interface ReaderTaskEither<R, E, A> {
  (r: R): TaskEither<E, A>
}
```

Added in v2.0.0

# URI (type alias)

**Signature**

```ts
export type URI = typeof URI
```

Added in v2.0.0

# URI

**Signature**

```ts
export declare const URI: 'ReaderTaskEither'
```

Added in v2.0.0

# alt

**Signature**

```ts
export declare const alt: <R, E, A>(
  that: () => ReaderTaskEither<R, E, A>
) => (fa: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# ap

**Signature**

```ts
export declare const ap: <R, E, A>(
  fa: ReaderTaskEither<R, E, A>
) => <B>(fab: ReaderTaskEither<R, E, (a: A) => B>) => ReaderTaskEither<R, E, B>
```

Added in v2.0.0

# apFirst

**Signature**

```ts
export declare const apFirst: <R, E, B>(
  fb: ReaderTaskEither<R, E, B>
) => <A>(fa: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# apSecond

**Signature**

```ts
export declare const apSecond: <R, E, B>(
  fb: ReaderTaskEither<R, E, B>
) => <A>(fa: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, B>
```

Added in v2.0.0

# ask

**Signature**

```ts
export declare const ask: <R, E = never>() => ReaderTaskEither<R, E, R>
```

Added in v2.0.0

# asks

**Signature**

```ts
export declare const asks: <R, E = never, A = never>(f: (r: R) => A) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# bimap

**Signature**

```ts
export declare const bimap: <E, G, A, B>(
  f: (e: E) => G,
  g: (a: A) => B
) => <R>(fa: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, G, B>
```

Added in v2.0.0

# bracket

Make sure that a resource is cleaned up in the event of an exception (_). The release action is called regardless of
whether the body action throws (_) or returns.

(\*) i.e. returns a `Left`

**Signature**

```ts
export declare function bracket<R, E, A, B>(
  aquire: ReaderTaskEither<R, E, A>,
  use: (a: A) => ReaderTaskEither<R, E, B>,
  release: (a: A, e: Either<E, B>) => ReaderTaskEither<R, E, void>
): ReaderTaskEither<R, E, B>
```

Added in v2.0.4

# chain

**Signature**

```ts
export declare const chain: <R, E, A, B>(
  f: (a: A) => ReaderTaskEither<R, E, B>
) => (ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, B>
```

Added in v2.0.0

# chainEitherK

**Signature**

```ts
export declare function chainEitherK<E, A, B>(
  f: (a: A) => Either<E, B>
): <R>(ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, B>
```

Added in v2.4.0

# chainFirst

**Signature**

```ts
export declare const chainFirst: <R, E, A, B>(
  f: (a: A) => ReaderTaskEither<R, E, B>
) => (ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# chainIOEitherK

**Signature**

```ts
export declare function chainIOEitherK<E, A, B>(
  f: (a: A) => IOEither<E, B>
): <R>(ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, B>
```

Added in v2.4.0

# chainTaskEitherK

**Signature**

```ts
export declare function chainTaskEitherK<E, A, B>(
  f: (a: A) => TaskEither<E, B>
): <R>(ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, B>
```

Added in v2.4.0

# filterOrElse

**Signature**

```ts
export declare const filterOrElse: {
  <E, A, B>(refinement: Refinement<A, B>, onFalse: (a: A) => E): <R>(
    ma: ReaderTaskEither<R, E, A>
  ) => ReaderTaskEither<R, E, B>
  <E, A>(predicate: Predicate<A>, onFalse: (a: A) => E): <R>(ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, A>
}
```

Added in v2.0.0

# flatten

**Signature**

```ts
export declare const flatten: <R, E, A>(
  mma: ReaderTaskEither<R, E, ReaderTaskEither<R, E, A>>
) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# fold

**Signature**

```ts
export declare function fold<R, E, A, B>(
  onLeft: (e: E) => ReaderTask<R, B>,
  onRight: (a: A) => ReaderTask<R, B>
): (ma: ReaderTaskEither<R, E, A>) => ReaderTask<R, B>
```

Added in v2.0.0

# fromEither

**Signature**

```ts
export declare const fromEither: <R, E, A>(ma: Either<E, A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# fromEitherK

**Signature**

```ts
export declare function fromEitherK<E, A extends ReadonlyArray<unknown>, B>(
  f: (...a: A) => Either<E, B>
): <R>(...a: A) => ReaderTaskEither<R, E, B>
```

Added in v2.4.0

# fromIOEither

**Signature**

```ts
export declare function fromIOEither<R, E, A>(ma: IOEither<E, A>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# fromIOEitherK

**Signature**

```ts
export declare function fromIOEitherK<E, A extends ReadonlyArray<unknown>, B>(
  f: (...a: A) => IOEither<E, B>
): <R>(...a: A) => ReaderTaskEither<R, E, B>
```

Added in v2.4.0

# fromOption

**Signature**

```ts
export declare const fromOption: <E>(onNone: () => E) => <R, A>(ma: Option<A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# fromPredicate

**Signature**

```ts
export declare const fromPredicate: {
  <E, A, B>(refinement: Refinement<A, B>, onFalse: (a: A) => E): <U>(a: A) => ReaderTaskEither<U, E, B>
  <E, A>(predicate: Predicate<A>, onFalse: (a: A) => E): <R>(a: A) => ReaderTaskEither<R, E, A>
}
```

Added in v2.0.0

# fromReaderEither

**Signature**

```ts
export declare function fromReaderEither<R, E, A>(ma: ReaderEither<R, E, A>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# fromTaskEither

**Signature**

```ts
export declare const fromTaskEither: <R, E, A>(ma: TE.TaskEither<E, A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# fromTaskEitherK

**Signature**

```ts
export declare function fromTaskEitherK<E, A extends ReadonlyArray<unknown>, B>(
  f: (...a: A) => TaskEither<E, B>
): <R>(...a: A) => ReaderTaskEither<R, E, B>
```

Added in v2.4.0

# getApplyMonoid

**Signature**

```ts
export declare function getApplyMonoid<R, E, A>(M: Monoid<A>): Monoid<ReaderTaskEither<R, E, A>>
```

Added in v2.0.0

# getApplySemigroup

**Signature**

```ts
export declare function getApplySemigroup<R, E, A>(S: Semigroup<A>): Semigroup<ReaderTaskEither<R, E, A>>
```

Added in v2.0.0

# getOrElse

**Signature**

```ts
export declare function getOrElse<R, E, A>(
  onLeft: (e: E) => ReaderTask<R, A>
): (ma: ReaderTaskEither<R, E, A>) => ReaderTask<R, A>
```

Added in v2.0.0

# getReaderTaskValidation

**Signature**

```ts
export declare function getReaderTaskValidation<E>(
  S: Semigroup<E>
): Monad3C<URI, E> & Bifunctor3<URI> & Alt3C<URI, E> & MonadTask3C<URI, E> & MonadThrow3C<URI, E>
```

Added in v2.3.0

# getSemigroup

**Signature**

```ts
export declare function getSemigroup<R, E, A>(S: Semigroup<A>): Semigroup<ReaderTaskEither<R, E, A>>
```

Added in v2.0.0

# left

**Signature**

```ts
export declare function left<R, E = never, A = never>(e: E): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# leftIO

**Signature**

```ts
export declare function leftIO<R, E = never, A = never>(me: IO<E>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# leftReader

**Signature**

```ts
export declare function leftReader<R, E = never, A = never>(me: Reader<R, E>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# leftReaderTask

**Signature**

```ts
export declare function leftReaderTask<R, E = never, A = never>(me: ReaderTask<R, E>): ReaderTaskEither<R, E, A>
```

Added in v2.5.0

# leftTask

**Signature**

```ts
export declare function leftTask<R, E = never, A = never>(me: Task<E>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# local

**Signature**

```ts
export declare function local<Q, R>(f: (f: Q) => R): <E, A>(ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<Q, E, A>
```

Added in v2.0.0

# map

**Signature**

```ts
export declare const map: <A, B>(f: (a: A) => B) => <R, E>(fa: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, E, B>
```

Added in v2.0.0

# mapLeft

**Signature**

```ts
export declare const mapLeft: <E, G>(
  f: (e: E) => G
) => <R, A>(fa: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, G, A>
```

Added in v2.0.0

# orElse

**Signature**

```ts
export declare function orElse<R, E, A, M>(
  onLeft: (e: E) => ReaderTaskEither<R, M, A>
): (ma: ReaderTaskEither<R, E, A>) => ReaderTaskEither<R, M, A>
```

Added in v2.0.0

# readerTaskEither

**Signature**

```ts
export declare const readerTaskEither: Monad3<'ReaderTaskEither'> &
  Bifunctor3<'ReaderTaskEither'> &
  Alt3<'ReaderTaskEither'> &
  MonadTask3<'ReaderTaskEither'> &
  MonadThrow3<'ReaderTaskEither'>
```

Added in v2.0.0

# readerTaskEitherSeq

Like `readerTaskEither` but `ap` is sequential

**Signature**

```ts
export declare const readerTaskEitherSeq: Monad3<'ReaderTaskEither'> &
  Bifunctor3<'ReaderTaskEither'> &
  Alt3<'ReaderTaskEither'> &
  MonadTask3<'ReaderTaskEither'> &
  MonadThrow3<'ReaderTaskEither'>
```

Added in v2.0.0

# right

**Signature**

```ts
export declare const right: <R, E = never, A = never>(a: A) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# rightIO

**Signature**

```ts
export declare function rightIO<R, E = never, A = never>(ma: IO<A>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# rightReader

**Signature**

```ts
export declare const rightReader: <R, E = never, A = never>(ma: Reader<R, A>) => ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# rightReaderTask

**Signature**

```ts
export declare function rightReaderTask<R, E = never, A = never>(ma: ReaderTask<R, A>): ReaderTaskEither<R, E, A>
```

Added in v2.5.0

# rightTask

**Signature**

```ts
export declare function rightTask<R, E = never, A = never>(ma: Task<A>): ReaderTaskEither<R, E, A>
```

Added in v2.0.0

# run

**Signature**

```ts
export declare function run<R, E, A>(ma: ReaderTaskEither<R, E, A>, r: R): Promise<Either<E, A>>
```

Added in v2.0.0

# swap

**Signature**

```ts
export declare function swap<R, E, A>(ma: ReaderTaskEither<R, E, A>): ReaderTaskEither<R, A, E>
```

Added in v2.0.0
