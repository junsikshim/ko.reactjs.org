---
id: faq-versioning
title: 버전 정책
permalink: docs/faq-versioning.html
layout: docs
category: FAQ
---

React는 [유의적 버전 (semver)](https://semver.org/) 원칙을 따릅니다.

즉, 버전 번호는 **x.y.z** 형태가 됩니다.

* **치명적인 버그를 수정**할 때는 **z** 번호를 바꾸고 **수 버전을 올려 배포**합니다. (예를 들어, 15.6.2에서 15.6.3)
* **새로운 기능**을 출시하거나 **치명적이지 않은 버그를 수정**할 때는 **y** 번호를 바꾸고 **부 버전을 올려 배포**를 합니다. (예를 들어, 15.6.2에서 15.7.0)
* **호환성이 유지되지 않는 변경**이 있을 때는 **x** 번호를 바꾸고 **주 버전을 올려 배포**를 합니다. (예를 들어, 15.6.2에서 16.0.0)

주 버전 배포는 새 기능을 포함할 수 있으며 모든 배포에는 버그 수정을 포함할 수도 있습니다.

부 버전을 변경시킨 배포가 가장 보편적인 배포 형태입니다.

해당 버전 정책은 Next 또는 Experimental 채널의 prerelease 빌드에는 적용되지 않습니다. [prerelease에 대해 여기서 알아보세요.](/docs/release-channels.html)

### 호환성이 유지되지 않는 변경 {#breaking-changes}

호환성이 유지되지 않는 변경은 모든 사람에게 불편할 수 있습니다. 그래서 주 버전 배포는 최소화하도록 노력합니다. 예를 들어, React 15는 2016년 4월에 배포되었고 React 16은 2017년 9월에 배포되었습니다. 그리고 React 17은 2020년 10월에 배포되었습니다.

대신 부 버전을 변경시킨 배포로 새 기능을 배포합니다. 부 버전 배포는 겸손한 이름에도 불구하고, 주 버전 배포보다 가끔 더 흥미롭고 주목할 만합니다.

### 안정성을 위한 노력 {#commitment-to-stability}

React가 서서히 변화하는 가운데 우리는 새 기능을 도입하기 위해 필요한 노력은 최소화하고 있습니다. 오래된 API를 다른 패키지로 분리하더라도, 오래된 API가 계속 동작하도록 가능한 유지할 예정입니다. 예를 들어, [믹스인은 수년 동안 그 기세가 꺾여오고 있지만](/blog/2016/07/13/mixins-considered-harmful.html), [create-react-class](/docs/react-without-es6.html#mixins)를 통해서 오늘날까지 지원되고 있고, 많은 코드 베이스가 안정된 레거시 코드에서 오래된 API를 계속 사용되고 있습니다.

백만 명 이상의 개발자가 React를 사용하고 있고, React에는 통틀어 수백만 개의 컴포넌트가 유지되고 있습니다. 페이스북 코드 베이스만 고려해 봐도 50,000개 이상의 React 컴포넌트가 있습니다. 이것은 React의 새 버전으로의 업그레이드를 가능한 한 쉽게 만들 필요가 있음을 의미합니다. 마이그레이션 수단도 없이 대단위의 큰 변화가 발생한다면 개발자들은 구버전에 갇히게 될 것입니다. 우리는 이 업그레이드 방법을 페이스북 자체에 테스트하고 있습니다. 열 명도 되지 않는 우리 팀이 단독적으로 5만 개 이상의 컴포넌트를 업데이트할 수 있다면 React를 사용하는 모든 개발자가 업그레이드를 관리할 수 있기를 기대합니다. 대부분의 경우, 컴포넌트 구문을 업그레이드하기 위한 [자동화 스크립트](https://github.com/reactjs/react-codemod)를 오픈소스 배포에 포함해서 누구나 사용할 수 있도록 하고 있습니다.

### 경고를 통한 점진적인 업그레이드 {#gradual-upgrades-via-warnings}

React 개발 빌드는 상당수의 유용한 경고를 포함합니다. 가능한 한 미래의 큰 변화에 대비하여 경고를 추가합니다. 최신 배포에서 여러분의 앱이 경고를 표시하지 않았다면 다음에 배포될 주 버전과 호환될 겁니다. 경고 덕분에 여러분은 컴포넌트 하나씩 앱을 업그레이드할 수 있게 해줍니다.

개발 경고는 앱의 런타임 수행에 영향을 주지는 않습니다. 다만, 그로 인해 앱의 개발 빌드와 프로덕션 빌드가 동일한 방식으로 동작할 거라는 확신을 가질 수 있습니다. 개발 빌드와 유일한 차이점이라면 프로덕션 빌드는 경고를 출력하지 않으며 조금 더 효율적입니다. (또 다른 점이 발견된다면 이슈를 제출해주세요)

### 무엇이 호환되지 않는 변화일까요? {#what-counts-as-a-breaking-change}

보통 우리는 다음의 변경에는 주 버전 번호를 *변화시키지 않습니다*.

* **개발 환경에서의 경고**. 프로덕션 빌드의 동작에는 영향을 미치지 않기 때문에 주요 버전 간에 새로운 경고를 추가하거나 기존 경고를 수정할 수 있습니다. 실제로, 이를 통해 다가올 호환되지 않는 변화에 대해 확실하게 경고할 수 있게 해줍니다.
* **`unstable_`로 시작하는 API**. 아직 신뢰할 수 있지 않은 API를 실험적인 기능으로 제공합니다. `unstable_` 접두어를 사용한 버전을 배포해서 개발 주기를 조금 더 빠르게 하고 안정적인 API를 조금 더 빠르게 얻을 수 있습니다.
* **React의 알파 버전과 카나리아(canary) 버전**. 새 기능의 이른 테스트를 위한 방법으로 React의 알파 버전을 제공합니다. 그러나 동시에, 알파 기간에 습득한 것을 바탕으로 변경을 자유롭게 할 수 있는 유연함도 필요합니다. 알파 버전을 사용하고 있다면 안정 버전이 출시되기 전에는 API가 얼마든지 변경될 수 있으니 주의해주세요.
* **문서화되지 않은 API와 내부 데이터 구조**. `__SECRET_INTERNALS_DO_NOT_USE_OR_YOU_WILL_BE_FIRED` 라든지 `__reactInternalInstance$uk43rzhitjg`와 같은 내부 프로퍼티에 접근한다면 책임은 스스로 지셔야 합니다.

이 정책은 실용적으로 설계되었습니다. 특히, 여러분의 머리가 아프지 않았으면 합니다. 이 모든 변화에 대해 주 버전 번호를 변화시킨다면, 더 많은 주 버전을 배포하게 되고 결국 커뮤니티에 버전 관리에 대한 고통을 더 가져다줄 겁니다. 이것은 우리가 바라는 만큼 빠르게 React를 발전시킬 수 없다는 것을 의미하기도 합니다.

그런데도 위의 목록과 같은 변경이 커뮤니티에서 광범위한 문제를 일으키게 된다면 점진적으로 마이그레이션 할 수 있는 수단을 제공할 수 있도록 최선을 다할 것입니다.

### 부 버전 배포에 새로운 기능이 포함되어 있지 않다면, 왜 수 버전을 변경하지 않나요? {#minors-versus-patches}

부 버전 배포에 새 기능이 포함되지 않을 수도 있습니다. [유의적 버전 관리에서 허용되며](https://semver.org/#spec-item-7), **"[부 버전]은 개인 코드에 상당한 새 기능이나 개선이 도입되는 경우 증가할 수 있다. 수 버전 수준의 변경이 포함될 수 있다."**라고 기재되어 있습니다.

그렇지만, 이런 배포는 왜 수 버전으로 배포하지 않는지 의문을 제기합니다.

정답은 React (또는 다른 소프트웨어)의 변경은 예상하지 못한 방식으로 고장 낼 위험이 있습니다. 하나의 버그를 수정하는 수 버전 배포가 실수로 다른 버그를 만들어내는 시나리오를 상상해 보세요. 이것은 개발자에게 혼란을 줄 뿐만 아니라 수 버전 배포에 대한 개발자의 신뢰를 떨어뜨립니다. 특히 원래의 해결책이 거의 마주치지 않는 버그에 대한 수정이라면 더욱 유감스러운 일입니다.

우리는 React 배포를 버그 없이 지켜온 꽤 좋은 기록을 가지고 있지만, 대부분의 개발자는 수 버전 배포가 부정적인 결과 없이 적용할 수 있다고 가정하기 때문에 수 버전 배포는 안정성에 대한 기준이 훨씬 높습니다.

이런 이유로 가장 중요한 버그와 보안 취약점에 대해서만 수 버전 배포를 사용합니다.

내부 코드 리팩토링이나 구현 세부사항에 대한 변화, 성능 개선, 사소한 버그 수정처럼 핵심적이지 않은 변경이 포함된 배포라면, 새로운 기능이 없을 때라도 부 버전을 증가시킬 겁니다.
