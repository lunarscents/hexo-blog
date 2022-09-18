---
title: TypeScript Basics
categories:
  - TypeScript
tags:
  - TypeScript
  - Front-End
thumbnail: /images/typescript.jpg
toc: true
date: 2020-06-05 19:08:56
---

## Overview

기존의 자바스크립트로 만든 프로젝트는 규모가 커지고 코드가 복잡해질수록 디버그와 테스트 단계에 검수 시간이 늘어났었습니다.

이를 극복하고자 나온 자바스크립트 대체 언어 중 하나가 `TypeScript(타입스크립트)`입니다.
<br/>

<!-- more -->

## What is the TypeScript?

{% blockquote %}
타입스크립트는 Microsoft에서 발표한 오픈소스로, JavaScript 프로그래밍 확장(Superset) 언어
{% endblockquote %}

1. `정적 타입`

   - 정적 타입을 지원하여 컴파일 단계에서 오류를 확인 가능합니다
   - 명시적인 정적 타입 지정은 개발자의 의도를 명확하게 전달하며, 코드 가독성을 높이고 디버깅을 쉽게 할 수 있도록 도와줍니다.

2. `도구의 지원`

   - IDE(Integrated Development Environment)와 같은 다양한 도구의 타입 정보를 제공 받아 높은 수준의 코드 어시스트, 타입 체크, 리팩토링 등을 지원받을 수 있으며 이러한 도구의 지원은 대규모 프로젝트를 위한 필수 요소입니다.

3. `강력한 객체지향 프로그래밍 지원`

   - 인터페이스, 제네릭 등과 같은 객체지향 프로그래밍을 지원하여 크고 복잡한 프로젝트의 코드 기반을 쉽게 구성할 수 있도록 합니다.

4. `ES6 / ES NEXT 지원`

   - TypeScript를 이용하여 새로운 스펙의 유용한 기능을 안정적으로 도입하기에 유리합니다. (TypeScript가 ECMAScript 표준에는 포함되어 있지 않지만, 표준화가 유력한 스펙을 도입하고 있습니다.)

<br/>

---

<br/>

## Requirements

`컴파일(Compile) / 트랜스파일(Transpile)` : TypeScript로 작성된 `.ts` 파일은 컴파일러를 이용해 JavaScript 파일로 변환해주어야 브라우저에서 동작 합니다.

### Setup(설치)

- NPM을 통한 설치
  {% gdemo_terminal 'npm install --save typescript' '70px' 'zsh' '500' '$' 'terminal1' %}
  {% endgdemo_terminal %}

- Yarn을 통한 설치
  {% gdemo_terminal 'yarn add typescript' '70px' 'zsh' '500' '$' 'terminal2' %}
  {% endgdemo_terminal %}

**tsconfig.json 환경설정**

- 해당 디렉토리에서 아래 명령어를 실행하면, `tsconfig.json` 파일이 자동 생성됩니다.

{% gdemo_terminal 'tsc --init' '70px' 'zsh' '500' '$' 'terminal3' %}
{% endgdemo_terminal %}

{% codeblock tsconfig.json lang:typescript https://www.typescriptlang.org/ko/docs/handbook/tsconfig-json.html tsconfig-json %}
{
"compilerOptions": {
/_ Basic Options _/
// "incremental": true, /_ Enable incremental compilation _/
"target": "ES2016", /_ Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019' or 'ESNEXT'. _/
"module": "commonjs", /_ Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'. _/
// "lib": [], /_ Specify library files to be included in the compilation. _/
// "allowJs": true, /_ Allow javascript files to be compiled. _/
// "checkJs": true, /_ Report errors in .js files. _/
// "jsx": "preserve", /_ Specify JSX code generation: 'preserve', 'react-native', or 'react'. _/
// "declaration": true, /_ Generates corresponding '.d.ts' file. _/
// "declarationMap": true, /_ Generates a sourcemap for each corresponding '.d.ts' file. _/
// "sourceMap": true, /_ Generates corresponding '.map' file. _/
// "outFile": "./", /_ Concatenate and emit output to single file. _/
"outDir": "./dist", /_ Redirect output structure to the directory. _/
// "rootDir": "./", /_ Specify the root directory of input files. Use to control the output directory structure with --outDir. _/
// "composite": true, /_ Enable project compilation _/
// "tsBuildInfoFile": "./", /_ Specify file to store incremental compilation information _/
// "removeComments": true, /_ Do not emit comments to output. _/
// "noEmit": true, /_ Do not emit outputs. _/
// "importHelpers": true, /_ Import emit helpers from 'tslib'. _/
// "downlevelIteration": true, /_ Provide full support for iterables in 'for-of', spread, and destructuring when targeting 'ES5' or 'ES3'. _/
// "isolatedModules": true, /_ Transpile each file as a separate module (similar to 'ts.transpileModule'). _/
/_ Strict Type-Checking Options _/
"strict": true, /_ Enable all strict type-checking options. _/
// "noImplicitAny": true, /_ Raise error on expressions and declarations with an implied 'any' type. _/
// "strictNullChecks": true, /_ Enable strict null checks. _/
// "strictFunctionTypes": true, /_ Enable strict checking of function types. _/
// "strictBindCallApply": true, /_ Enable strict 'bind', 'call', and 'apply' methods on functions. _/
// "strictPropertyInitialization": true, /_ Enable strict checking of property initialization in classes. _/
// "noImplicitThis": true, /_ Raise error on 'this' expressions with an implied 'any' type. _/
// "alwaysStrict": true, /_ Parse in strict mode and emit "use strict" for each source file. _/
/_ Additional Checks _/
// "noUnusedLocals": true, /_ Report errors on unused locals. _/
// "noUnusedParameters": true, /_ Report errors on unused parameters. _/
// "noImplicitReturns": true, /_ Report error when not all code paths in function return a value. _/
// "noFallthroughCasesInSwitch": true, /_ Report errors for fallthrough cases in switch statement. _/
/_ Module Resolution Options _/
// "moduleResolution": "node", /_ Specify module resolution strategy: 'node' (Node.js) or 'classic' (TypeScript pre-1.6). _/
// "baseUrl": "./", /_ Base directory to resolve non-absolute module names. _/
// "paths": {}, /_ A series of entries which re-map imports to lookup locations relative to the 'baseUrl'. _/
// "rootDirs": [], /_ List of root folders whose combined content represents the structure of the project at runtime. _/
// "typeRoots": [], /_ List of folders to include type definitions from. _/
// "types": [], /_ Type declaration files to be included in compilation. _/
// "allowSyntheticDefaultImports": true, /_ Allow default imports from modules with no default export. This does not affect code emit, just typechecking. _/
"esModuleInterop": true /_ Enables emit interoperability between CommonJS and ES Modules via creation of namespace objects for all imports. Implies 'allowSyntheticDefaultImports'. _/
// "preserveSymlinks": true, /_ Do not resolve the real path of symlinks. _/
// "allowUmdGlobalAccess": true, /_ Allow accessing UMD globals from modules. _/
/_ Source Map Options _/
// "sourceRoot": "", /_ Specify the location where debugger should locate TypeScript files instead of source locations. _/
// "mapRoot": "", /_ Specify the location where debugger should locate map files instead of generated locations. _/
// "inlineSourceMap": true, /_ Emit a single file with source maps instead of having a separate file. _/
// "inlineSources": true, /_ Emit the source alongside the sourcemaps within a single file; requires '--inlineSourceMap' or '--sourceMap' to be set. _/
/_ Experimental Options _/
// "experimentalDecorators": true, /_ Enables experimental support for ES7 decorators. _/
// "emitDecoratorMetadata": true, /_ Enables experimental support for emitting type metadata for decorators. _/
}
}
{% endcodeblock %}

**컴파일 및 실행**

- 아래와 같은 `sample.ts` 파일을 작성 한 후, `tsc` 명령어를 실행합니다.

{% codeblock src/sample.ts lang:typescript %}
const message: string = 'Hello, LunarScents!';

console.log(message);
{% endcodeblock %}

- 타입스크립트 CLI를 통해 코드를 컴파일 하기 위해서는 타입스크립트를 전역으로 설치하거나, 또는 아래와 같이 package.json의 build 스크립트를 작성합니다.

{% codeblock package.json lang:typescript %}

{
"name": "typescript-sample",
"version": "1.0.0",
"main": "index.js",
"license": "MIT",
"dependencies": {
"typescript": "^3.6.4"
},
"scripts": {
"build": "tsc"
}
}

{% endcodeblock %}

## Basic Types

JavaScript 에서 지원하는 기본형 타입(`Boolean, Number, String, Array, Null, Undefined`)을 지원하며, 추가적으로 지원하는 타입들은 아래와 같습니다.

- 두 가지의 타입은 `|` 연산자를 사용합니다.

### Tuple

- 튜플 타입은 고정된 개수의 요소 타입을 알고 있지만 반드시 같을 필요는 없는 배열을 표현할 수 있도록 합니다.
- 예를 들어, 다음과 같은 string과 number의 쌍으로 값을 나타낼 수 있습니다

```typescript
// 튜플 타입 선언
let x: [string, number];

// 초기화
x = ['hello', 10]; // 좋아요
// 부정확한 초기화
x = [10, 'hello']; // 오류
```

### Enum

- JavaScript의 표준 데이터 타입 집합에 추가할 수 있는 유용하고 부가적인 추가 자료는 `enum` 입니다.
- 멤버 중 하나의 값을 수동으로 설정하여 이를 변경할 수 있거나, 열거 형의 모든 값을 수동으로 설정합니다.(기본적으로 enums는 0부터 시작하는 자신의 멤버 번호를 매기기를 시작합니다.)
- enum의 편리한 기능은 숫자 값에서 enum의 해당 값 이름으로 이동할 수 있다는 것입니다.

```typescript
enum Color {
  Red = 1,
  Green,
  Blue
}

let colorName: string = Color[2];

console.log(colorName); // 위의 값이 2 이므로 'Green'을 표시합니다.
```

### Any

- 코드를 작성할 때 알지 못하는 변수의 타입을 설명해야 할 수도 있습니다.
- 타입 검사를 선택하지 않고 그 값이 컴파일-타임 검사를 통과하도록 하고 싶은 경우, `any` 타입으로 지정합니다.
- any 타입은 기존 JavaScript로 작업할 수 있는 강력한 방법으로 컴파일 과정에서 타입 검사를 점진적으로 실행 (opt-in) 및 중지(opt-out) 할 수 있습니다.
- 객체와 다른 점은 객체는 객체 타입의 변수를 사용하면 해당 객체에는 값만 할당할 수 있습니다.

```typescript
let notSure: any = 4;

notSure.ifItExists(); // 좋아요, 런타임에 ifItExists가 존재할 수 있습니다.
notSure.toFixed(); // 좋아요, toFixed는 존재합니다. (그러나 컴파일러는 체크하지 않습니다)
let prettySure: Object = 4;

prettySure.toFixed(); // 오류: 'Object' 타입에 'toFixed' 프로퍼티는 존재하지 않습니다.
```

### Void

- `void`는 `any`의 정반대이지만 조금 비슷합니다.
- 반환 값을 반환하지 않는 함수의 반환 타입으로 볼 수 있습니다.
- `void` 타입의 변수 선언은 `undefined` 또는 `null` 만 할당할 수 있으므로 유용하지 않습니다.

```typescript
function warnUser(): void {
  console.log('This is my warning message');
}

let unusable: void = undefined;
```

### Never

- `never` 타입은 절대로 발생하지 않는 값의 타입을 나타냅니다.
- 예를 들어, 함수 표현식의 반환 타입이거나 항상 예외를 던지는 화살표 함수 표현식이거나 절대 반환하지 않는 표현식입니다.
- 변수는 또한 `never` 일 때 타입 가드에 의해 좁혀지더라도 결코 사실일 수 없으며 타입을 획득하지 못합니다.
- `never` 타입은 모든 타입의 서브 타입이며 모든 타입에 할당할 수 있습니다.
- 어떤 타입도 never의 서브 타입이거나 할당 가능한 타입은 아닙니다.
- `any` 조차도 `never`에 할당할 수 없습니다.

```typescript
// 반환되는 함수에는 연결할 수 없는 end-point가 있어서는 안 됩니다.
function error(message: string): never {
  throw new Error(message);
}

// 추론되는 반환 타입은 절대로 없습니다.
function fail() {
  return error('Something failed');
}

// 반환되는 함수에는 연결할 수 없는 end-point가 있어서는 안 됩니다.
function infiniteLoop(): never {
  while (true) {}
}
```

### Type assertions

- `Type assertions` 은 컴파일러에게 "나를 믿어, 내가 하고 있는 일을 안다"라고 말하는 방법입니다.
- `Type assertions` 은 다른 언어의 형 변환(타입캐스팅)과 비슷하지만 특별한 검사나 데이터를 재구성하지는 않습니다.
- 런타임에 영향을 미치지 않으며 컴파일러에서만 사용됩니다.
- TypeScript는 개발자가 필요한 특별한 검사를 수행했다고 가정합니다.
- Type assertions은 두 가지 형태를 가집니다.

  - `angle-bracket(꺾쇠괄호)` 구문

    ```typescript
    let someValue: any = 'this is a string';

    let strLength: number = (<string>someValue).length;
    ```

  - `as` 구문
  - TypeScript를 JSX와 함께 사용할 때는 as 스타일의 assertions(단언)만 허용합니다.

    ```typescript
    let someValue: any = 'this is a string';

    let strLength: number = (someValue as string).length;
    ```

## Functions

## Interface

`Inerface` 는 클래스 나 객체를 위한 타입을 지정할 때 사용하는 문법입니다.

## Generics

`Generics` 는 타입스크립트에서 함수, 클래스, interface, type을 사용하게 될 때 여러 종류의 타입에 대하여 호환을 맞춰야 하는 상황에서 사용하는 문법입니다.

---

## References

- [TypeScript 공식](https://www.typescriptlang.org/index.html)
- [TypeScript](https://typescript-kr.github.io)
- [5분 안에 보는 TypeScript](https://typescript-kr.github.io/pages/tutorials/TypeScript%20in%205%20minutes.html)
- [TypeScript 소개와 개발환경 구축](https://freestrokes.tistory.com/94)
- [2019년과 이후 JavaScript의 동향 - 라이브러리와 프레임워크 2](https://d2.naver.com/helloworld/2108442)
