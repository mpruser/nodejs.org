---
title: ECMAScript 2015 (ES6) 및 그 이후
layout: learn
authors: ovflowd
---

# ECMAScript 2015 (ES6) 및 그 이후

Node.js는 최신 버전의 [V8](https://v8.dev/)에 기반하여 구축되었습니다. 이 엔진의 최신 릴리스를 지속적으로 따라감으로써, 우리는 [JavaScript ECMA-262 사양](http://www.ecma-international.org/publications/standards/Ecma-262.htm)에서 새로운 기능이 Node.js 개발자에게 시기적절하게 제공되도록 하고, 지속적인 성능 및 안정성 개선을 보장합니다.

모든 ECMAScript 2015 (ES6) 기능은 **배송**(shipping), **단계적**(staged), 및 **진행 중**(in progress) 기능의 세 그룹으로 나뉩니다:

- V8가 안정적으로 간주하는 모든 **배송** 기능은 Node.js에서 **기본적으로 활성화**되어 있으며, 어떤 형태의 런타임 플래그도 필요하지 않습니다.
- V8 팀에서 안정적으로 간주되지 않는 거의 완료된 기능인 **단계적** 기능은 런타임 플래그 `--harmony`가 필요합니다.
- **진행 중**인 기능은 각자의 하모니 플래그로 개별적으로 활성화할 수 있지만, 테스트 용도로만 사용하는 것이 강력히 권장됩니다. 참고: 이러한 플래그는 V8에 의해 노출되며, 어떠한 경고 없이 변경될 수 있습니다.

### 어떤 기능이 어떤 Node.js 버전과 함께 기본적으로 제공되나요?

웹사이트 [node.green](https://node.green/)는 다양한 Node.js 버전에서 지원되는 ECMAScript 기능에 대한 훌륭한 개요를 제공합니다. 이 정보는 kangax의 compat-table을 기반으로 합니다.

### 어떤 기능이 진행 중인가요?

새로운 기능은 V8 엔진에 지속적으로 추가되고 있습니다. 일반적으로 이러한 기능이 향후 Node.js 릴리스에 포함될 것으로 예상되지만, 시기는 알 수 없습니다.

각 Node.js 릴리스에서 사용 가능한 모든 _진행 중_ 기능을 나열하려면 `--v8-options` 인수를 통해 grep을 사용하여 확인할 수 있습니다. 이러한 기능은 미완성이거나 결함이 있을 수 있으므로, 사용 시 주의가 필요합니다:

```bash
node --v8-options | grep "in progress"
```

### 내 인프라가 --harmony 플래그를 활용하도록 설정되어 있습니다. 이를 제거해야 할까요?

Node.js에서 `--harmony` 플래그의 현재 동작은 **단계적** 기능만 활성화하는 것입니다. 결국, 이는 `--es_staging`의 동의어입니다. 위에서 언급한 것처럼, 이러한 기능은 완료되었지만 안정성이 고려되지 않은 기능입니다. 특히 운영 환경에서는 V8이 기본적으로 제공할 때까지 이 런타임 플래그를 제거하는 것이 안전할 수 있습니다. 이 플래그를 유지하면 V8가 표준에 더 가깝게 변경됨에 따라 코드가 깨질 수 있는 Node.js 업그레이드에 대비해야 합니다.

### 특정 Node.js 버전에 포함된 V8 버전을 어떻게 찾나요?

Node.js는 특정 바이너리와 함께 제공되는 모든 의존성과 해당 버전을 나열하는 간단한 방법을 제공합니다. V8 엔진의 경우, 다음 명령어를 터미널에 입력하여 버전을 확인할 수 있습니다:

```bash
node -p process.versions.v8
```
