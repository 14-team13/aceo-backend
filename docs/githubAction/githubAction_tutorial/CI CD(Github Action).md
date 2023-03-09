# CI/CD(Github Action)

## ❓CI/CD란?

> CI(Continuous Integeration), CD(Continuous Delivery)의 합성어로, 소프트웨어 개발 프로세스에서 자동화된 빌드, 테스트 및 배포를 위한 접근 방식.

✔️ **CI** ❓ **개발자가 코드를 변경할 때마다 자동으로 코드를 빌드하고, 테스트하여 코드 변경에 대한 오류나 충돌을 즉시 발견하고 수정할 수 있도록 해줌**. 
지속적으로 코드를 통합함으로써 코드 품질을 높이고, 버그를 조기에 발견하여 비용과 시간을 절약하는 이점이 있음.

✔️**CD** ❓ 지속적인 배포를 가능하게 해주는 프로세스로, **AP개발이 완료된 후 자동으로 빌드, 테스트, 배포가 이루어져 사용자에게 지속적으로 안정적인 배포를 제공할 수 있도록 해줌**.
이를 통해 사용자에게 제공되는 서비스 품질을 개선하고, 배포 주기를 단축하여 더 빠르게 개발 및 서비스를 제공할 수 있음.
> 

## 🏁 CI/CD 툴 소개

1. Jenkins
    
    <aside>
    💡 가장 오랫동안 널리 사용되어 온 툴로 수많은 플러그인과 documnet가 제공된다는 장점이 있지만, 설치형이기 때문에 플러그인 버전관리에 따른 의존성 문제가 있고 초반 설정이 어려움.
    
    </aside>
    
2. Github action
    
    <aside>
    💡 Github에서 제공하는 툴로 github과 강하게 결합되어 연동이 간편함. 클라우드 서버 사용으로 설치가 필요 없고 설정이 쉽다는 장점이 있지만, Jenkins에 비해 역사가 오래되지 않아 레퍼런스가 부족하다는 단점이 있음.
    
    </aside>
    

### 🤷‍♀️ Jenkins vs Github Action

| Jenkins | GitHub Actions |
| --- | --- |
| 서버 설치가 필요 | 클라우드에서 동작하므로 어떤 설치도 필요 없음 |
| 작업이 동기적으로 일어나므로, 제품을 시장까지 배포하는 데에 더 많은 시간이 소요됨 | 비동기 CI/CD 가능함 |
| 계정과 트리거에 기반하고 있으며 GitHub 이벤트를 처리할 수 없음 | 모든 GitHub 이벤트에 대해 GitHub Actions를 제공하고 있으며 많은 언어와 프레임워크도 지원함 |
| 환경 호환성을 위해 Docker 이미지에서 동작해야 함 | 모든 환경에 호환됨 |
| 캐싱 기법을 위해 플러그인을 제공하고 있음. | 캐싱이 필요하다면 직접 캐싱 메커니즘을 작성해야 함 |
| 공유할 수 있는 기능을 제공하고 있지 않음 | GitHub 마켓플레이스를 통해 공유할 수 있음 |

## ✅ Github Action 기본개념

- **WorkFlow** ❓  자동화해놓은 작업 과정으로 최상위 개념. 하나의 코드 저장소에는 여러 개의 워크플로우, 즉 여러 개의 YAML 파일을 생성할 수 있음.
- **Jobs** ❓독립된 가상머신 또는 컨테이너에서 돌아가는 하나의 처리 단위, 하나의 워크플로우는 여러개의 작업으로 구성됨.
- **Steps** ❓각 작업을 구성하는 스텝, 단순한 커맨드나 스크립트가 될 수도 있고 액션이 될수도 있음. 액션일 경우 **run** 속성을, 커맨드나 스크립스 사용시에는 **uses**속성을 사용함.
- **Actions** ❓빈번하게 필요한 반복 단계를 재사용하기 용이하도록 제공되는 일종의 작업 공유 매커니즘. 하나의 코드저장소 범위 내에서 재사용 뿐 아니라 마켓플레이스를 통해 공개된 액션을 사용할 수도 있음.

## ✨ Github Action 사용방법

1. Github Repo > Action Tab > new workflow
- 워크플로우 생성
    
    ![스크린샷 2023-02-23 09.25.36.png](./CI%20CD(Github%20Action)/step1.png)
    
2. 프로젝트에 맞는 워크플로우 선택 > configuration
   - 프로젝트를 분석해서 추천해줌 (SpringBoot라서 그래들로 추천)
    
    ![스크린샷 2023-02-23 09.25.47.png](./CI%20CD(Github%20Action)/step2.png)
    
3. 최초 YAML 파일 생성 > 마켓플레이스에서 적당한 액션 검색 가능함.  
**자세한 스크립트는 [깃헙 레포](https://github.com/Hyesooo/github_action_practice.git) 주석 참고**
    
    
    ![스크린샷 2023-02-23 09.25.56.png](./CI%20CD(Github%20Action)/step3.png)
    
4. 해당 브랜치에 Push이벤트 발생시에 워크플로우 동작 및 결과 확인 가능.
    
    ![스크린샷 2023-02-23 09.23.50.png](./CI%20CD(Github%20Action)/step4.png)
    
    ![스크린샷 2023-02-23 09.25.11.png](./CI%20CD(Github%20Action)/step6.png)
    

📚 Reference

- [https://hyperconnect.github.io/2021/11/08/github-actions-for-everyone-1.html](https://hyperconnect.github.io/2021/11/08/github-actions-for-everyone-1.html)
- [https://thalals.tistory.com/383](https://thalals.tistory.com/383)
- [https://rutgo-letsgo.tistory.com/80](https://rutgo-letsgo.tistory.com/80)
- [https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)
- [https://www.daleseo.com/github-actions-basics/](https://www.daleseo.com/github-actions-basics/)