# 타입스크립트 기초
## 타입지정

오브젝트 형
```
let test : {member1 : string, member2 : string} = {member1 : 'kim', member2 : 'park'} // 1개의 타입
let obj : {a : string|number, b : string} = {a : 123, b : 'string'}  // 2개의 타입
```
배열
```
let array : string[] = ['kim', 'park'] // 1개의 타입
let array2 : (string|number)[] = [1, '2', 3] // 2개의 타입
```

## 내로잉
함수에 받는 파라미터가 number인지 string 인지 두가지 이상의 타입이 존재할 시 조건문으로 진입을 좁혀줘야한다
```
const 함수 = (x : number|string) => {
        if(typeof x === 'string'){
            console.log('string')
        } else if (typeof x === 'number'){
            console.log('number')
        }
        
        let test = x as number //assertion 문법 x를 number로 해주세요~
        
    }
```

## 타입 변수로 저장하기
```
type Man = {name : string, age : number}
...
let 사람 : Man = {name : 'kim', age : 20}
```
type XXX 에 기본타입뿐 아닌 지정한 문자열이나 숫자를 넣을 수 있음

## type과 interface
```
interface Student {name : string}
interface Teacher extends Student {age : number}
```
인터페이스는 extends를 사용해서 중복되는 부분을 하나로 합칠 수 있음

```
type Animal = {name : string}
type Cat = {age : number} & Animal
```
type은 & 이라는 intersection 타입을 사용해서 둘다 사용할 수 있음

## JSX 타입지정
```
let 박스 :JSX.Element = <div></div>
let 버튼 :JSX.Element = <button></button>

더 정확히 하려면 아래와같이 사용합니다

let 박스 :JSX.IntrinsicElements['div'] = React.createElement('div');
let 버튼 :JSX.IntrinsicElements['button'] = <button></button>;
```
## 함수형 컴포넌트의 타입지정
```
type AppProps = {
  name: string;
}; 

function App (props: AppProps) :JSX.Element {
  return (
    <div>{message}</div>
  )
}
```
## useState의 타입지정
```
const [user, setUser] = useState<string | null>('kim');
```

