---
title: "Visual Studio Code 확장 팩 만들기"
date: 2025-01-20T13:38:56+09:00
draft: true
---

Visual Studio Code(VSCode)는 다양한 확장을 지원하여 생산성을 높이고 개발 워크플로우를 간소화하는 강력한 코드 편집기입니다. 함께 잘 작동하는 확장 모음을 가지고 있다면, 확장 팩을 만들어 사용자가 이를 쉽게 설치하고 관리할 수 있도록 할 수 있습니다.
<!--more-->

이번 포스트에서는 자신만의 VSCode 확장 팩을 만드는 방법을 단계별로 안내하겠습니다.

## 1단계: 환경 설정

확장 팩을 만들기 전에 다음 도구들이 설치되어 있는지 확인하세요:

1. **Node.js**: [nodejs.org](https://nodejs.org/)에서 Node.js를 다운로드하고 설치합니다.
2. **Visual Studio Code**: 아직 설치하지 않았다면 [code.visualstudio.com](https://code.visualstudio.com/)에서 VSCode를 다운로드합니다.
3. **Yeoman 및 VSCode 확장 생성기**: 터미널을 열고 다음 명령어를 실행하여 Yeoman과 생성기를 설치합니다:

    ```bash
    npm install -g yo generator-code
    ```

## 2단계: 확장 팩 생성

환경 설정이 완료되었으니 이제 확장 팩을 생성해 보겠습니다:

1. **새 확장 팩 생성**: 터미널에서 다음 명령어를 실행합니다:

    ```bash
    yo code
    ```

   - 프롬프트가 나타나면 **New Extension Pack**을 선택합니다.
   - 확장 팩의 이름, 설명 및 기타 세부 정보를 입력합니다.

2. **`package.json` 수정**: 생성기가 완료되면 확장 팩의 디렉토리로 이동하여 `package.json` 파일을 엽니다. 다음과 유사한 구조를 볼 수 있습니다:

   ```json
   {
     "name": "your-extension-pack-name",
     "displayName": "Your Extension Pack",
     "description": "A pack of useful extensions.",
     "version": "0.0.1",
     "publisher": "your-publisher-name",
     "engines": {
       "vscode": "^1.60.0"
     },
     "extensionPack": [
       "publisher.extension1",
       "publisher.extension2"
     ],
     "activationEvents": [],
     "main": "./out/extension.js",
     "contributes": {
       "commands": [],
       "configuration": {}
     }
   }
   ```

   - **`extensionPack`**: 여기에서 포함할 확장의 식별자를 추가합니다. 형식은 `publisher.extensionName`입니다.

## 3단계: 확장 팩 테스트

1. **VSCode에서 확장 팩 열기**: VSCode에서 확장 팩이 포함된 폴더를 엽니다.
2. **확장 실행**: `F5` 키를 눌러 확장 팩이 로드된 새로운 VSCode 창을 시작합니다. 이를 통해 기능을 테스트하고 포함된 모든 확장이 인식되는지 확인할 수 있습니다.

## 4단계: 확장 팩 게시

확장 팩에 만족하면 이제 게시할 차례입니다:

1. **VSCE 도구 설치**: 아직 설치하지 않았다면, 확장을 패키징하고 게시하기 위한 VSCE 도구를 설치합니다:

   ```bash
   npm install -g @vscode/vsce
   ```

2. **확장 패키지 만들기**: 터미널에서 다음 명령어를 실행합니다:

   ```bash
   vsce package
   ```

   이 명령어는 디렉토리에 `.vsix` 파일을 생성합니다.

3. **확장 팩 게시**: 확장 팩을 게시하려면 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)에서 게시자 계정을 생성해야 합니다. 게시 지침에 따라 다음 명령어를 사용하여 확장 팩을 게시합니다:

   ```bash
   vsce publish
   ```

## 추가 팁

- **문서화**: 확장 팩에 대한 명확한 문서를 제공하여 설치 및 사용 방법을 안내합니다.
- **버전 관리**: `package.json` 파일에서 버전 관리를 통해 업데이트를 효과적으로 관리합니다.
- **테스트**: 모든 포함된 확장이 예상대로 작동하는지 철저히 테스트합니다.

## 결론

VSCode 확장 팩을 만드는 것은 관련 확장을 묶어 사용자 경험을 향상시키는 좋은 방법입니다. 이 포스트에서 설명한 단계를 따르면 쉽게 자신만의 확장 팩을 생성하고 테스트하며 게시할 수 있습니다. 즐거운 코딩 되세요!

---

필요에 따라 내용을 수정하거나 개인적인 통찰을 추가하여 더 매력적으로 만들 수 있습니다! 추가적인 도움이 필요하시면 언제든지 말씀해 주세요.
