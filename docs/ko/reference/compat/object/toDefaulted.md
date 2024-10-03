# toDefaulted

::: info
이 함수는 호환성을 위한 `es-toolkit/compat` 에서만 가져올 수 있어요. 대체할 수 있는 네이티브 JavaScript API가 있거나, 아직 충분히 최적화되지 않았기 때문이에요.

`es-toolkit/compat`에서 이 함수를 가져오면, [lodash와 완전히 똑같이 동작](../../../compatibility.md)해요.
:::

객체 `object`를 기반으로, 특정 프로퍼티들에 대해서 `undefined`를 반환하지 않도록 기본값을 설정한 새 객체를 반환해요.
`undefined`이거나 `Object.prototype`에서 상속받은 값에 대해서 기본값을 설정해요.

기본값을 설정하기 위해서 여러 객체를 파라미터로 제공할 수 있어요. 이 객체들은 왼쪽에서 오른쪽 순서대로 적용돼요.
어떤 프로퍼티에 값이 지정되면, 같은 프로퍼티에 대해서 이후 값들은 무시돼요.

주의: 이 함수는 새로운 객체를 생성해요. 객체 `object`를 수정하고 싶다면 [defaults](./defaults.md) 함수를 사용하세요.

## 인터페이스

```typescript
function toDefaulted<T extends object>(object: T): NonNullable<T>;
function toDefaulted<T extends object, S extends object>(object: T, source: S): NonNullable<T & S>;
function toDefaulted<T extends object, S1 extends object, S2 extends object>(
  object: T,
  source1: S1,
  source2: S2
): NonNullable<T & S1 & S2>;
function toDefaulted<T extends object, S1 extends object, S2 extends object, S3 extends object>(
  object: T,
  source1: S1,
  source2: S2,
  source3: S3
): NonNullable<T & S1 & S2 & S3>;
function toDefaulted<T extends object, S1 extends object, S2 extends object, S3 extends object, S4 extends object>(
  object: T,
  source1: S1,
  source2: S2,
  source3: S3,
  source4: S4
): NonNullable<T & S1 & S2 & S3 & S4>;
function toDefaulted<T extends object, S extends object>(object: T, ...sources: S[]): object;
```

### 파라미터

- `object` (`T`): 대상 객체.
- `sources` (`S[]`): 기본값을 지정하는 객체들.

### 반환 값

(`object`): 대상 객체가 `sources`가 지정한 기본값을 가지도록 새로 생성한 객체.

## 예시

```typescript
toDefaulted({ a: 1 }, { a: 2, b: 2 }, { c: 3 }); // { a: 1, b: 2, c: 3 }
toDefaulted({ a: 1, b: 2 }, { b: 3 }, { c: 3 }); // { a: 1, b: 2, c: 3 }
toDefaulted({ a: null }, { a: 1 }); // { a: null }
toDefaulted({ a: undefined }, { a: 1 }); // { a: 1 }
```