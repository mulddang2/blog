---
layout: post
title: "[JavaScript] javascript 모듈화, class 활용"
date: 2023-05-29 19:31:29 +0900
category: JavaScript
---
## Module
관련 없는 모든 프로그램을 하나의 모듈/파일에 함께 두는 것보다 각 작업에 대해 여러 파일 또는 모듈을 만드는 것이 좋습니다. 
기본 앱 또는 프로그램에서 필요한 모듈을 가져오고 로드하고 그에 따라 실행하기만 하면 됩니다.
따라서 모듈화를 하면 더 코드가 깔끔해지고 단순해집니다. 또한 다른 프로그램에서도 이전에 모듈화해 놓은 것과 동일한 기능을 재사용하기가 매우 쉬워집니다. 그렇기 때문에 모듈화를 제대로 해놓는다면 다시 코딩할 필요가 없어집니다.

## JavaScript Modules
자바스크립트에서 모듈은 관련 코드를 포함하는 파일 뿐입니다.
또한 서로 다른 모듈에서 각각 기능을 내보내고 받기 위해 `import` 및 `export` 키워드를 사용합니다.

-  `export` 키워드는 다른 모듈에서 변수, 함수, 클래스 또는 객체에 액세스할 수 있도록 만드는 데 사용됩니다. 즉, 공개 코드가 됩니다.
- `import` 키워드는 다른 모듈에서 공개 코드를 가져오는 데 사용됩니다.


```javascript
class NumberUtils {
  static getPower(decimalPlaces) {
    return 10 ** decimalPlaces;
  }
  
  static roundToDecimalPlace(number, decimalPlaces = 2) {
    const round = NumberUtils.getPower(decimalPlaces);
    return Math.round(number * round) / round;
  }
}

export default class StringUtils {
  static capitalize(word) {
    return word[0].toUpperCase() + word.slice(1);
  }
}

export { StringUtils, NumberUtils };

```


이 모듈에는 세가지 기능이 정의되어 있습니다.
- getPower: 이 함수는 숫자의 거듭제곱을 얻습니다. 
- capitalize: 이 함수는 단어의 첫 글자를 대문자로 만듭니다. 
- roundToDecimalPlace: 이 함수는 주어진 숫자를 지정된 소수 자릿수로 반올림합니다.

파일 끝에서 세가지 기능 중 두가지 기능이 내보내진 것을 볼 수 있습니다. 즉, 다른 스크립트에서도 사용할 수 있는 공용 함수가 되었습니다.

### export 하는법
세 가지 중 두 가지 기능을 내보내려면 export 키워드를 사용하고, 그 뒤에 엑세스 할 수 있는 기능이 포함된 개체를 사용합니다. 

```javascript
export { StringUtils, NumberUtils };
```

### import 하는 법
```javascript
import StringUtils, { NumberUtils } from './test.js';

const word = 'hoo';
const capitalizedWord = StringUtils.capitalize(word);
console.log(capitalizedWord); // 출력: 'Hoo'

const number = 3.14159;
const numberUtils = new NumberUtils();
const roundedNumber = numberUtils.roundToDecimalPlace(number, 2);
console.log(roundedNumber); // 출력: 3.14

```

import 키워드 다음에 모듈에서 가져오려는 함수의 이름을 사용합니다.
위 코드에 따르면, 아까 export한 capitalize, roundToDecimalPlace를 가져오고자 합니다.

### * keyword
다른 모듈에서 모든 public 함수 가져올 때 사용합니다.
```
import * as StringUtils from './test.js';
```
### default keyword
모듈의 기능을 모두 내보내고 싶지만, 그 중 하나를 기본값으로 만들고자 할 때 사용합니다.
```javascript
export default class StringUtils {
  static capitalize(word) {
    return word[0].toUpperCase() + word.slice(1);
  }
}
```
default 한 capitalize 함수를 가져올 때, 중괄호 없이 가져오면 됩니다.
```javascript
import StringUtils from './test.js';
```

근데 만약, 기본함수를 다른 함수와 함께 가져와야할 때는?
아래와 같이 기본함수와 중괄호 안에 있는 다른 함수를 혼합하여 사용합니다.

```javascript
import StringUtils, { NumberUtils } from './test.js';
```

## 마무리
모듈은 독립적이고 독립적인 코드 덩어리입니다. 더 큰 프로그램을 논리적 부분 또는 종속성으로 분할하여 생성합니다.

모듈은 독립적이고 특수하며 재사용 가능해야 합니다.

import 와 export 키워드로 JavaScript의 모듈 간에 기능을 교환합니다.

default 키워드를 사용하여 첫 번째 선택 가져오기가 될 함수, 개체, 변수 또는 클래스를 지정합니다.

<br />
<br /> 

**참고자료**
<hr />
- JavaScript Modules – Explained with Examples<br />
[https://www.freecodecamp.org/news/javascript-modules-explained-with-examples/](https://www.freecodecamp.org/news/javascript-modules-explained-with-examples/){:target="\_blank"}
- ChatGPT - 예제코드 오류수정