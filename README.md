# effective-typescript

## 이펙티브 타입스크립트를 읽고 정리 

### 추론 가능한 타입을 사용해 장황한 코드 방지하기 

**모든 변수, 특히 함수 내의 지역변수에 타입을 선언하는것은 비생산적이다.**

```javascript
 let x: number = 10; 
```

타입이 추론이 된다면 명시적 타입 구문은 필요하지 않다.
```javascript
 let x = 10; 
```

**비구조화 할당문을 사용하여 모든 지역 변수의 타입이 추론되도록 한다**
비구조화 할당문은 모든 지역 변수의 타입이 추론되도록 한다. 
비구조화 할당문을 사용했다면 타입 내의 속성의 타입이 변경되도 타입 체커를 통과할 수 있다. 
```javascript
 interface Product {
  id: string;
  name: string;
  price: number;
}

function printProduct(product: Product) {
  const {id, name, price} = product;
  console.log(id, name, price);
}
```

**함수 반환시 타입을 명시하여 오류 방지하기**
반환 타입을 명시하면 오류가 발생한 정확한 위치를 파악할 수 있다.


## 다른 타입에는 다른 변수 사용하기

**타입스크립트에서는 하나의 변수를 다른 타입으로 재사용하면 오류가 발생한다. union 타입을 활용해 타입을 확장하여 사용할 수 있지만, 해당 변수를 사용할때마다 값이 어떤 타입인지 확인해야 하기 때문에 
union타입은 다루기 까다롭다. 따라서 별도의 변수를 만드는것이 더 좋다.**
