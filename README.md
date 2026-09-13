**# Python & Git 기초 — 나만의 프롬프트 관리 프로그램**

**## 1. 프로젝트 소개**

이 프로젝트는 Python 기초 문법과 Git/GitHub 사용법을 익히기 위해 제작한 콘솔 기반 프롬프트 관리 프로그램입니다.

이전 AI 미션에서 작성한 프롬프트를 한곳에 모아 관리하고, 새로운 프롬프트를 추가하거나 카테고리별로 조회하고, 키워드 검색·상세 보기·즐겨찾기 등의 기능을 사용할 수 있도록 구현합니다.

또한 프로그램을 기능 단위로 개발하면서 Git으로 변경 이력을 기록하고, 별도의 Branch에서 기능을 개발한 뒤 \`main\` Branch에 병합하는 과정을 실습합니다.

과제에서는 프롬프트를 카테고리별로 분류하고 검색·즐겨찾기하면서 데이터 처리 논리를 익히고, 동시에 Git으로 코드의 변경 이력을 관리하는 것을 주요 학습 목표로 합니다.

**---**

**## 2. 프로그래밍 언어에 친숙하지 않은 사람을 위한 핵심 용어 설명**

이번 보고서는 Python이나 Git을 처음 접하는 사람도 이해할 수 있도록 주요 용어를 먼저 설명합니다.

\| 용어 | 쉬운 설명 | 이번 과제에서의 역할 |

\|---|---|---|

\| *\*\****\*\*Python\*\***\*\* | 사람이 작성한 명령을 컴퓨터가 실행할 수 있도록 프로그램을 만드는 프로그래밍 언어 | 프롬프트 관리 프로그램 제작 |

\| *\*\****\*\*VS Code\*\***\*\* | 프로그램 코드를 작성하고 수정·실행할 수 있는 코드 편집 프로그램 | Python 코드 작성 및 실행 |

\| *\*\****\*\*콘솔(Console)\*\***\*\* | 버튼 대신 글자나 번호를 입력하여 프로그램을 사용하는 방식 | 메뉴 번호를 입력하여 기능 선택 |

\| *\*\****\*\*터미널(Terminal)\*\***\*\* | 명령어를 글자로 입력하여 컴퓨터에 작업을 지시하는 창 | Python 실행 및 Git 명령어 입력 |

\| *\*\****\*\*Git\*\***\*\* | 코드가 언제 어떻게 변경되었는지 기록하는 버전 관리 도구 | 기능별 개발 과정 기록 |

\| *\*\****\*\*GitHub\*\***\*\* | Git으로 관리한 프로젝트를 온라인에 저장·공유할 수 있는 서비스 | 과제 코드 업로드 및 제출 |

\| *\*\****\*\*Repository\*\***\*\* | Git이 프로젝트 파일과 변경 기록을 관리하는 저장소 | 프로젝트 관리 |

\| *\*\****\*\*Commit\*\***\*\* | 특정 시점의 변경사항을 하나의 기록으로 저장하는 것 | 기능별 작업 기록 |

\| *\*\****\*\*Branch\*\***\*\* | 기존 코드를 유지하면서 별도의 작업 공간에서 기능을 개발하는 방법 | 프롬프트 목록 기능 별도 개발 |

\| *\*\****\*\*Merge\*\***\*\* | 다른 Branch에서 작업한 내용을 현재 Branch에 합치는 것 | 목록 기능을 \`main\`에 병합 |

과제에서는 Git이 무엇이고 왜 필요한지 설명할 수 있어야 하며, \`init\`, \`add\`, \`commit\`, \`push\`, \`pull\`, \`checkout\`, \`clone\`, \`merge\`가 각각 어떤 역할을 하는지도 설명할 수 있어야 합니다.

**---**

**## 3. 개발 환경**

\| 항목 | 사용 환경 |

\|---|---|

\| OS | Windows 10 |

\| Python | Python 3.14.7 |

\| Editor | Visual Studio Code |

\| VS Code Python Extension | 설치 |

\| Korean Language Pack | 설치 |

\| Git | Git 2.55.0.windows.4 |

\| GitHub | GitHub CLI 인증 및 원격 Repository 연동 완료 |

\| 기본 Branch | \`main\` |

**### 3.1 개발 도구 설치**

프롬프트 관리 프로그램을 개발하기 위해 Python, Visual Studio Code, Git을 설치했습니다.

Python은 프로그램을 작성하고 실행하기 위한 프로그래밍 언어이며, Visual Studio Code는 Python 코드를 작성·수정·실행하기 위한 코드 편집 프로그램입니다. Git은 프로그램을 개발하면서 변경 이력을 기록하고 Branch와 Merge 등의 버전 관리 기능을 사용하기 위해 설치했습니다.

**#### 📷 Python 설치 증빙**

![Python 3.14.7 설치 완료]\(images/02-python-installation.jpg)

**\*\*그림 1. Python 3.14.7 설치 완료\*\***

Python 3.14.7 설치가 정상적으로 완료된 화면입니다. 설치 후 터미널에서 \`python --version\` 명령어를 실행하여 실제 설치된 버전도 다시 확인했습니다.

**#### 📷 Visual Studio Code 설치 증빙**

![Visual Studio Code 설치]\(images/03-vscode-installation.jpg)

**\*\*그림 2. Visual Studio Code 설치\*\***

Python 코드를 작성하고 실행하기 위해 Visual Studio Code를 설치하는 과정입니다. 이후 VS Code에서 프로젝트 폴더를 열고 Python 파일 작성과 터미널 명령 실행에 사용했습니다.

**#### 📷 Git 설치 증빙**

![Git 2.55.0 설치 완료]\(images/04-git-installation.jpg)

**\*\*그림 3. Git 2.55.0 설치 완료\*\***

Git 설치가 정상적으로 완료된 화면입니다. 설치 후 \`git --version\` 명령어를 실행하여 Git이 정상적으로 사용할 수 있는 상태인지 다시 확인했습니다.

**---**

**### 3.2 개발 환경 설정 및 Python 실행 확인**





개발 도구를 설치한 뒤 Git을 사용하기 위한 사용자 정보와 기본 Branch를 설정했습니다.

Git에서 Commit 작성자를 구분할 수 있도록 사용자 이름과 이메일을 먼저 설정했습니다.

\`\`\`bash

git config --global user.name "사용자 이름"

git config --global user.email "사용자 이메일"

\`\`\`

새로운 Git 저장소를 만들었을 때 기본 Branch가 \`main\`이 되도록 설정했습니다.

\`\`\`bash

git config --global init.defaultBranch main

\`\`\`

설정 후 다음 명령어를 사용하여 Python과 Git의 설치 상태 및 Git 설정값을 확인했습니다.

\`\`\`bash

python --version

git --version

git config --global user.name

git config --global user.email

git config --global init.defaultBranch

\`\`\`

그 다음 현재 \`python-git-prompt-manager\` 프로젝트 폴더를 Git으로 관리하기 위해 Git 저장소를 초기화했습니다.

\`\`\`bash

git init

\`\`\`

Git 저장소를 초기화한 뒤 현재 Branch를 확인했습니다.

\`\`\`bash

git branch --show-current

\`\`\`

확인 결과 현재 Branch가 다음과 같이 \`main\`으로 설정되어 있었습니다.

\`\`\`text

main

\`\`\`

마지막으로 Python이 정상적으로 프로그램을 실행할 수 있는지 확인하기 위해 \`hello.py\` 파일을 작성했습니다.

\`\`\`python

print("Hello")

\`\`\`

터미널에서 다음 명령어로 실행했습니다.

\`\`\`bash

python .\hello.py

\`\`\`

실행 결과:

\`\`\`text

Hello

\`\`\`

**#### 📷 개발 환경 설정 및 Python 실행 증빙**

![개발 환경 설정 및 Python 실행 확인]\(images/01-development-environment.png)

**\*\*그림 4. 개발 환경 설정 및 Python 실행 확인\*\***

위 화면에서는 다음 내용을 한 번에 확인할 수 있습니다.

\- Python 3.14.7 버전 확인

\- Git 2.55.0.windows.4 버전 확인

\- Git 사용자 이름 설정 및 확인

\- Git 사용자 이메일 설정 및 확인

\- 기본 Branch를 \`main\`으로 설정 및 확인

\- \`git init\`을 통한 프로젝트 Git 저장소 초기화

\- 현재 Branch가 \`main\`인지 확인

\- \`hello.py\` 실행 후 \`Hello\`가 정상적으로 출력되는지 확인

Git을 처음 사용하는 경우 단순히 확인 명령어부터 실행하기보다 *\*\****\*\*사용자 이름·이메일 및 기본 Branch 설정 → 설정값 확인 → \`git init\` → 현재 Branch 확인\*\***\*\* 순서로 진행하는 것이 좋습니다. 특히 Git 저장소가 아닌 폴더에서 Branch 관련 명령어를 먼저 실행하면 오류가 발생할 수 있으므로, 프로젝트 폴더를 Git 저장소로 초기화한 뒤 확인했습니다.





**---**

**### 3.3 Git 추적 대상 등록 및 \`.gitignore\` 확인**

프로젝트의 초기 파일을 작성한 뒤 Git으로 변경 이력을 관리하기 위해 다음 명령어를 실행했습니다.

\`\`\`bash

git add .

git status

\`\`\`

\`git add .\`는 현재 프로젝트의 변경사항을 다음 Commit에 포함할 대상으로 등록하는 명령어입니다.

\`git status\`는 어떤 파일이 Git의 추적 대상이 되었는지와 어떤 변경사항이 Commit을 위해 준비되어 있는지 확인하는 명령어입니다.

**#### 📷 Git Commit 대상 파일 확인**

![Git Add 및 Status 확인]\(images/05-git-add-status.png)

**\*\*그림 5. \`git add .\` 및 \`git status\` 실행 결과\*\***

\`git add .\` 실행 후 \`git status\`를 사용하여 \`.gitignore\`, \`README.md\`, \`hello.py\`, \`main.py\`, \`images/\` 폴더의 증빙 자료가 Commit 대상으로 등록된 것을 확인했습니다.

이 과정에서 Windows가 자동으로 생성한 \`images/desktop.ini\` 파일도 Commit 대상에 포함된 것을 발견했습니다.

**---**

**#### 📷 불필요한 시스템 파일 제외 설정**

![desktop.ini Git 제외 설정]\(images/06-gitignore-desktop-ini.jpg)

**\*\*그림 6. \`.gitignore\`에 \`desktop.ini\` 제외 규칙 추가\*\***

\`desktop.ini\`는 Windows가 폴더 설정 정보를 저장하기 위해 자동으로 생성하는 시스템 파일로, 이번 Python 프로그램의 실행에 필요한 파일이 아닙니다.

불필요한 시스템 파일이 GitHub Repository에 포함되지 않도록 \`.gitignore\`에 다음 항목을 추가했습니다.

\`\`\`gitignore

desktop.ini

\`\`\`

\`.gitignore\`는 Git으로 관리할 필요가 없는 파일이나 폴더를 추적 대상에서 제외하기 위한 설정 파일입니다.

여기서 *\*\****\*\*제외한다는 것은 컴퓨터에서 해당 파일을 삭제한다는 뜻이 아닙니다.\*\***\*\*

\`.gitignore\`의 목적은 파일을 컴퓨터에서 없애는 것이 아니라 *\*\****\*\*Git이 해당 파일을 추적하거나 Commit 대상으로 등록하지 않도록 하는 것\*\***\*\*입니다.

따라서 \`desktop.ini\` 파일은 실제 \`images/\` 폴더에 남아 있어도 문제가 없습니다.

\`git status\`에서 \`desktop.ini\`가 나타나지 않는다면 \`.gitignore\`가 정상적으로 적용된 것입니다.

**---**

**#### 📷 \`.gitignore\` 적용 결과 확인**

![Gitignore 적용 결과 확인]\(images/07-gitignore-verification.jpg)

**\*\*그림 7. \`desktop.ini\` 제외 후 Git 상태 확인\*\***

\`.gitignore\`를 수정한 뒤 다시 \`git status\`를 실행했습니다.

확인 결과 이전에는 Commit 대상에 표시되었던 \`images/desktop.ini\`가 더 이상 표시되지 않았으며, 실제 프로젝트에 필요한 파일만 Commit 대상으로 남은 것을 확인했습니다.

이 과정을 통해 단순히 \`.gitignore\` 파일을 작성하는 것에서 끝내지 않고,

**\*\*불필요한 파일 발견 → \`.gitignore\` 수정 → \`git status\`를 통한 적용 결과 확인\*\***

순서로 설정이 실제로 적용되었는지 검증했습니다.

**---**

**#### 📷 첫 Commit 전 최종 Staging 상태 확인**

![첫 Commit 전 Git Staging 상태]\(images/08-git-staging-final.jpg)

**\*\*그림 8. 첫 Commit 전 Git Staging 상태 최종 확인\*\***

\`.gitignore\` 설정을 적용한 뒤 다시 \`git add .\`와 \`git status\`를 실행하여 첫 Commit에 포함될 파일을 확인했습니다.

확인 결과 \`.gitignore\`, \`README.md\`, \`hello.py\`, \`main.py\`와 \`images/\` 폴더의 증빙 자료가 Commit 대상으로 등록되었으며, Windows가 자동으로 생성한 \`desktop.ini\`는 Commit 대상에서 제외된 것을 확인했습니다.

또한 실제 작업 중 발생한 \`not a git repository\` 오류 화면은 이후 문제 해결 및 시행착오 과정을 설명하기 위한 증빙 자료로 보관했습니다.

**---**

**#### 📷 첫 Commit 전 Staging 완료 확인**

![Git Staging 완료 확인]\(images/09-git-staging-complete.jpg)

**\*\*그림 9. 첫 Commit 전 Git Staging 완료 확인\*\***

README와 새로운 증빙 자료를 추가한 뒤 \`git add .\`을 다시 실행하고 \`git status\`로 최종 상태를 확인했습니다.

확인 결과 프로젝트의 초기 파일과 증빙 자료가 모두 \`Changes to be committed\`에 표시되었습니다.

이는 해당 파일들이 다음 Commit에 포함될 수 있도록 *\*\****\*\*Staging Area(스테이징 영역)\*\***\*\*에 등록되었다는 의미입니다.

여기서 *\*\****\*\*Staging\*\***\*\*은 변경된 파일 중 다음 Commit에 포함할 파일을 미리 선택하여 준비하는 과정입니다.

\`git add .\`은 현재 프로젝트의 변경사항을 Staging Area에 등록하고, \`git status\`는 등록 상태를 확인하는 데 사용합니다.

또한 \`desktop.ini\`는 실제 \`images/\` 폴더에는 남아 있지만 \`.gitignore\` 설정에 따라 Git의 추적 대상에서는 제외되어 \`git status\`에 나타나지 않는 것을 다시 확인했습니다.

따라서 불필요한 Windows 시스템 파일은 제외하면서 과제 수행에 필요한 파일과 증빙 자료만 첫 Commit에 포함할 준비가 완료되었습니다.





**### 3.4 첫 Commit 및 Git 기록 확인**

프로젝트 초기 파일과 증빙 자료가 Staging Area에 정상적으로 등록된 것을 확인한 뒤 첫 Commit을 생성했습니다.

첫 Commit에는 프로젝트 기본 구조, \`README.md\`, \`.gitignore\`, Python 실행 확인 파일과 현재까지 작성한 증빙 자료를 기록했습니다.

다음 명령어를 실행했습니다.

\`\`\`bash

git commit -m "chore: initialize Python project"

\`\`\`

\`git commit\`은 Staging Area에 준비된 변경사항을 하나의 기록으로 저장하는 명령어입니다.

이번 Commit 메시지는 다음과 같이 작성했습니다.

\`\`\`text

chore: initialize Python project

\`\`\`

여기서 \`chore\`는 새로운 프로그램 기능을 추가한 작업이라기보다 프로젝트 설정이나 초기 구조를 구성하는 작업에 사용하는 표현입니다.

\`initialize Python project\`는 이번 Commit이 Python 프로젝트의 초기 구조를 구성한 작업이라는 의미입니다.

첫 Commit을 생성한 뒤 실제로 Git 기록에 저장되었는지 확인하기 위해 다음 명령어를 실행했습니다.

\`\`\`bash

git log --oneline

\`\`\`

\`git log\`는 지금까지 생성된 Commit 기록을 확인하는 명령어입니다.

여기에 \`--oneline\` 옵션을 사용하면 각 Commit을 한 줄로 간단하게 표시하여 *\*\****\*\*Commit 식별값과 Commit 메시지\*\***\*\*를 빠르게 확인할 수 있습니다.

**#### 📷 첫 Commit 및 Git Log 확인**

![첫 Commit 및 Git Log 확인]\(images/11-first-commit-and-git-log.jpg)

**\*\*그림 10. 첫 Commit 생성 및 Git 기록 확인\*\***

\`git commit -m "chore: initialize Python project"\`를 실행한 결과 첫 Commit이 정상적으로 생성된 것을 확인했습니다.

Commit 결과에 \`root-commit\`이 표시되었는데, 이는 현재 Repository에서 생성된 *\*\****\*\*첫 번째 Commit\*\***\*\*이라는 의미입니다.

이어서 \`git log --oneline\`을 실행하여 방금 생성한 \`chore: initialize Python project\` Commit이 Git 변경 이력에 정상적으로 저장되어 있는지 확인했습니다.

이를 통해 단순히 Commit 명령을 실행하는 것에서 끝내지 않고,

**\*\*Staging 완료 → 첫 Commit 생성 → Git Log를 통한 기록 확인\*\***

순서로 첫 번째 변경 이력이 정상적으로 저장되었는지 검증했습니다.





**### 3.5 GitHub CLI 설치 및 로그인**

GitHub Repository 생성과 원격 저장소 작업을 VS Code Terminal에서도 수행해보기 위해 GitHub CLI를 사용했습니다.

GitHub CLI는 GitHub 웹사이트에서 수행하는 일부 작업을 터미널 명령어로 실행할 수 있도록 해주는 도구입니다.

예를 들어 Repository 생성, GitHub 로그인 상태 확인, Pull Request 확인 등의 작업을 터미널에서 수행할 수 있습니다.

처음 다음 명령어를 실행했습니다.

\`\`\`bash

gh --version

\`\`\`

하지만 GitHub CLI가 설치되어 있지 않아 \`gh\` 명령어를 인식하지 못하는 오류가 발생했습니다.

이후 Windows의 \`winget\`을 사용하여 GitHub CLI를 설치했습니다.

\`\`\`powershell

winget install --id GitHub.cli

\`\`\`

설치가 완료된 뒤 새 터미널에서 다시 다음 명령어를 실행했습니다.

\`\`\`bash

gh --version

\`\`\`

확인 결과 다음과 같이 GitHub CLI 버전이 정상적으로 표시되었습니다.

\`\`\`text

gh version 2.100.0

\`\`\`

**#### 📷 GitHub CLI 설치 및 정상 동작 확인**

![GitHub CLI 설치 및 확인]\(images/12-github-cli-install-and-verification.jpg)

**\*\*그림 11. GitHub CLI 설치 및 정상 동작 확인\*\***

처음 \`gh --version\`을 실행했을 때 GitHub CLI가 설치되어 있지 않아 명령어를 인식하지 못하는 오류가 발생했습니다.

이후 \`winget install --id GitHub.cli\` 명령어를 사용하여 GitHub CLI를 설치했고, 새 터미널에서 다시 \`gh --version\`을 실행했습니다.

확인 결과 \`gh version 2.100.0\`이 정상적으로 출력되어 GitHub CLI가 설치되고 터미널에서 사용할 수 있는 상태임을 확인했습니다.

이 과정을 통해 Git과 GitHub CLI가 서로 다른 도구이며, GitHub CLI를 사용하려면 별도 설치가 필요하다는 점도 확인했습니다.

설치 후 GitHub 로그인 상태를 확인하기 위해 다음 명령어를 실행했습니다.

\`\`\`bash

gh auth status

\`\`\`

처음에는 GitHub 계정에 로그인되지 않은 상태였기 때문에 다음 명령어로 인증을 진행했습니다.

\`\`\`bash

gh auth login

\`\`\`

인증 과정에서는 GitHub.com, HTTPS, 브라우저 로그인 방식을 선택했고, 브라우저에서 Device Activation과 권한 승인 절차를 진행했습니다.

**#### 📷 GitHub CLI 로그인 및 인증 완료**

![GitHub CLI 로그인 성공]\(images/16-github-cli-login-success.jpg)

**\*\*그림 12. GitHub CLI 로그인 및 인증 완료\*\***

브라우저에서 GitHub Device Activation과 권한 승인 절차를 완료한 뒤 VS Code Terminal로 돌아왔습니다.

터미널에서 \`Authentication complete.\` 메시지가 표시되었고, Git 작업에 사용할 프로토콜이 HTTPS로 설정된 것도 확인했습니다.

또한 \`Logged in as ...\`가 표시되어 GitHub CLI가 실제 GitHub 계정에 정상적으로 로그인된 것을 확인했습니다.

이 과정을 통해 다음 순서로 GitHub CLI 인증을 완료했습니다.

**\*\*GitHub.com 선택 → HTTPS 선택 → 브라우저 인증 → 권한 승인 → 추가 본인 확인 → 인증 완료\*\***

중간 과정에서 사용한 \`13-github-device-activation.jpg\`, \`14-github-cli-authorization.jpg\`, \`15-github-cli-confirm-access.jpg\`는 GitHub CLI 로그인 절차를 단계별로 확인할 수 있는 참고 자료로 보관했습니다.

**#### 📷 GitHub CLI 로그인 상태 확인**

![GitHub CLI 로그인 상태 확인]\(images/17-github-auth-status.jpg)

**\*\*그림 13. \`gh auth status\`를 통한 로그인 상태 확인\*\***

GitHub CLI 인증을 완료한 뒤 다음 명령어를 다시 실행했습니다.

\`\`\`bash

gh auth status

\`\`\`

확인 결과 GitHub.com 계정이 활성 상태로 로그인되어 있었고, Git 작업에 사용할 프로토콜도 \`https\`로 설정되어 있음을 확인했습니다.

또한 인증에 필요한 토큰과 Repository 작업에 필요한 권한 범위가 정상적으로 설정된 것을 확인했습니다.

이를 통해 브라우저 인증이 완료되었다는 메시지만 확인하는 데서 끝내지 않고, \`gh auth status\`를 사용해 실제 GitHub CLI 로그인 상태를 다시 검증했습니다.

**#### 터미널에서 GitHub 작업을 진행한 이유**

이번 과제의 필수 요구사항만 수행한다면 GitHub 웹사이트에서 Repository를 생성해도 충분합니다.

하지만 Git과 GitHub를 처음 사용하는 입장에서 웹 화면뿐 아니라 VS Code Terminal에서도 GitHub 작업을 직접 수행해보면, 로컬 Git과 원격 GitHub가 어떻게 연결되는지 더 구체적으로 이해할 수 있다고 판단했습니다.

특히 GitHub CLI를 사용하면 Repository 생성, 로그인 상태 확인, 원격 저장소 작업 등을 명령어로 수행할 수 있으므로, 이후 반복적인 GitHub 작업을 더 빠르고 일관된 방식으로 처리하는 연습이 됩니다.

장점은 다음과 같습니다.

\- Git과 GitHub CLI의 역할 차이를 실제 작업을 통해 이해할 수 있습니다.

\- Repository 생성과 원격 연결 과정을 명령어 단위로 확인할 수 있습니다.

\- 반복 작업을 웹 화면보다 빠르게 수행할 수 있습니다.

\- 사용한 명령어가 터미널 기록에 남아 작업 과정을 다시 확인하기 쉽습니다.

\- 다른 사람이 같은 명령어를 따라 하며 실습하기 좋습니다.

다만 단점도 있습니다.

\- GitHub CLI를 별도로 설치하고 로그인해야 합니다.

\- 처음에는 명령어와 옵션을 익혀야 하므로 웹 화면보다 어렵게 느껴질 수 있습니다.

\- 명령어를 잘못 입력하면 원하지 않는 Repository나 원격 설정을 만들 수 있으므로 실행 전 확인이 필요합니다.

\- GitHub CLI 인증 과정에서 계정과 권한 범위를 확인해야 하므로 보안에 대한 주의가 필요합니다.

따라서 이번 과제에서는 *\*\****\*\*과제 필수 기능을 충족하는 것뿐 아니라 Git/GitHub 작업 흐름을 이해하기 위한 추가 학습 목적으로 GitHub CLI를 사용했습니다.\*\***\*\*

**### 3.6 GitHub Repository 생성 및 원격 저장소 연결**

GitHub CLI 로그인 상태를 확인한 뒤 VS Code Terminal에서 새로운 GitHub Repository를 생성했습니다.

이번에는 GitHub 웹사이트에서 직접 Repository를 만드는 대신, 앞에서 설치한 GitHub CLI를 활용하여 터미널에서 Repository 생성과 원격 저장소 연결 과정을 직접 수행했습니다.

다음 명령어를 실행했습니다.

\`\`\`bash

gh repo create python-git-prompt-manager --public --source=. --remote=origin

\`\`\`

각 항목의 의미는 다음과 같습니다.

\| 명령 및 옵션 | 의미 |

\|---|---|

\| \`gh repo create\` | GitHub에 새로운 Repository를 생성 |

\| \`python-git-prompt-manager\` | 생성할 Repository 이름 |

\| \`--public\` | Repository를 공개(Public) 상태로 생성 |

\| \`--source=.\` | 현재 프로젝트 폴더를 Repository의 기준으로 사용 |

\| \`--remote=origin\` | 생성된 GitHub Repository를 \`origin\`이라는 이름의 원격 저장소로 연결 |

여기서 *\*\****\*\*Remote(원격 저장소)\*\***\*\* 는 현재 컴퓨터에 있는 로컬 Git Repository와 연결되는 GitHub의 온라인 Repository를 의미합니다.

\`origin\`은 원격 저장소에 일반적으로 사용하는 기본 이름입니다. 즉, 이후 \`git push\`나 \`git pull\`을 사용할 때 \`origin\`을 통해 현재 로컬 프로젝트와 GitHub Repository 사이에 데이터를 주고받을 수 있습니다.

Repository를 생성한 뒤 원격 저장소가 실제로 연결되었는지 확인하기 위해 다음 명령어를 실행했습니다.

\`\`\`bash

git remote -v

\`\`\`

\`git remote -v\`는 현재 로컬 Repository에 연결된 원격 저장소의 이름과 주소를 확인하는 명령어입니다.

**#### 📷 GitHub Repository 생성 및 Remote 연결 확인**

![GitHub Repository 및 Remote 연결]\(images/18-github-repository-and-remote.jpg)

**\*\*그림 14. GitHub Repository 생성 및 원격 저장소 연결 확인\*\***

\`gh repo create\` 명령을 실행한 결과 GitHub에 \`python-git-prompt-manager\` Repository가 정상적으로 생성되었습니다.

또한 생성된 Repository가 현재 로컬 프로젝트에 \`origin\`이라는 이름으로 자동 연결된 것을 확인했습니다.

이후 \`git remote -v\`를 실행한 결과 \`origin\`에 대해 \`fetch\`와 \`push\` 주소가 모두 표시되었습니다.

여기서 \`fetch\`는 GitHub의 변경사항을 가져올 때 사용하는 주소이고, \`push\`는 로컬의 Commit을 GitHub로 전송할 때 사용하는 주소입니다.

이를 통해

**\*\*GitHub Repository 생성 → 원격 저장소 \`origin\` 연결 → \`git remote -v\`를 통한 연결 상태 확인\*\***

순서로 GitHub Repository와 로컬 프로젝트가 정상적으로 연결되었는지 검증했습니다.

**### 3.7 GitHub 설정 문서화 Commit 및 첫 Push**

GitHub Repository 생성과 원격 저장소 연결을 완료한 뒤, 지금까지 작성한 README와 GitHub CLI 관련 증빙 자료를 Git 변경 이력에 추가했습니다.

먼저 다음 명령어를 사용하여 변경된 파일을 Staging Area에 등록하고 상태를 확인했습니다.

\`\`\`bash

git add .

git status

\`\`\`

확인 결과 수정된 \`README.md\`와 GitHub CLI 설치·로그인·Repository 생성 과정의 증빙 이미지가 다음 Commit에 포함될 대상으로 등록되었습니다.

이후 다음 명령어로 두 번째 Commit을 생성했습니다.

\`\`\`bash

git commit -m "docs: document GitHub setup process"

\`\`\`

여기서 \`docs\`는 프로그램 기능 자체를 추가한 것이 아니라 README, 설명 문서, 증빙 자료와 같은 문서 작업을 기록할 때 사용하는 표현입니다.

\`document GitHub setup process\`는 GitHub CLI 설치, 로그인, Repository 생성 및 원격 저장소 연결 과정을 문서화했다는 의미입니다.

**#### 📷 GitHub 설정 문서화 Commit**

![GitHub 설정 문서화 Commit]\(images/19-github-setup-docs-commit.jpg)

**\*\*그림 15. GitHub 설정 과정 문서화 및 두 번째 Commit\*\***

\`git add .\`과 \`git status\`를 통해 변경사항을 확인한 뒤 \`docs: document GitHub setup process\`라는 메시지로 Commit을 생성했습니다.

이를 통해 GitHub 설정 과정을 README와 증빙 이미지에 기록한 작업도 별도의 변경 이력으로 관리했습니다.

**---**

두 번째 Commit까지 완료한 뒤 로컬 Repository의 Commit을 처음으로 GitHub 원격 Repository에 전송했습니다.

다음 명령어를 실행했습니다.

\`\`\`bash

git push -u origin main

\`\`\`

각 명령과 옵션의 의미는 다음과 같습니다.

\| 명령 및 옵션 | 의미 |

\|---|---|

\| \`git push\` | 로컬 Repository의 Commit을 GitHub 원격 Repository로 전송 |

\| \`-u\` | 현재 \`main\` Branch와 \`origin/main\`의 추적 관계를 설정 |

\| \`origin\` | 앞에서 연결한 GitHub 원격 저장소의 이름 |

\| \`main\` | GitHub로 전송할 현재 로컬 Branch |

여기서 \`-u\` 옵션을 처음 Push할 때 사용하면 로컬 \`main\` Branch와 GitHub의 \`origin/main\` Branch 사이에 추적 관계가 설정됩니다.

따라서 이후 같은 Branch에서 작업할 때는 원격 저장소와 Branch를 매번 모두 입력하지 않고 다음과 같이 간단하게 사용할 수 있습니다.

\`\`\`bash

git push

\`\`\`

첫 Push를 완료한 뒤 현재 상태를 확인하기 위해 다음 명령어도 실행했습니다.

\`\`\`bash

git status

\`\`\`

**#### 📷 첫 GitHub Push 및 상태 확인**

![첫 GitHub Push 및 상태 확인]\(images/20-first-github-push-and-status.jpg)

**\*\*그림 16. 첫 GitHub Push 성공 및 Push 이후 Git 상태 확인\*\***

\`git push -u origin main\`을 실행한 결과 다음 메시지가 표시되었습니다.

\`\`\`text

[new branch] main -> main

branch 'main' set up to track 'origin/main'.

\`\`\`

이는 로컬 \`main\` Branch가 GitHub의 \`origin/main\` Branch로 정상적으로 전송되었으며, 두 Branch 사이의 추적 관계도 설정되었다는 의미입니다.

이후 \`git status\`를 실행한 결과 다음 메시지가 표시되었습니다.

\`\`\`text

Your branch is up to date with 'origin/main'.

\`\`\`

따라서 당시 Commit된 Git 변경 이력은 GitHub와 정상적으로 동기화된 것을 확인했습니다.

다만 첫 Push 직후 새로 만든 증빙 이미지가 \`Untracked files\`에 표시되었습니다.

여기서 *\*\****\*\*Untracked file\*\***\*\*은 오류가 발생했다는 뜻이 아니라, 파일이 새로 생성되었지만 아직 \`git add\`와 Commit을 거치지 않았다는 의미입니다.

즉 첫 Push 자체는 정상적으로 성공했지만, 그 과정을 증빙하기 위해 새로 생성한 이미지도 다시 Git으로 관리할 필요가 있음을 확인했습니다.

**---**

첫 Push 증빙 자료와 README 수정 내용을 다시 Git 변경 이력에 포함하기 위해 다음 명령어를 실행했습니다.

\`\`\`bash

git add .

git status

git commit -m "docs: add first push evidence"

\`\`\`

Commit을 완료한 뒤에는 앞에서 \`-u\` 옵션을 사용하여 추적 관계를 이미 설정했기 때문에 다음과 같이 간단하게 Push할 수 있었습니다.

\`\`\`bash

git push

\`\`\`

이처럼 처음에는

\`\`\`bash

git push -u origin main

\`\`\`

을 사용하지만, 이후 같은 Branch에서는 추적 관계가 기억되어 있기 때문에 보통 다음 명령어만 사용하면 됩니다.

\`\`\`bash

git push

\`\`\`

마지막으로 로컬 Repository와 GitHub가 완전히 같은 상태인지 다시 확인했습니다.

\`\`\`bash

git status

\`\`\`

**#### 📷 추적 관계 설정 후 Push 및 최종 동기화 확인**

![GitHub Push 및 최종 동기화 확인]\(images/22-github-push-and-clean-status.jpg)

**\*\*그림 17. \`git push\` 실행 및 로컬·GitHub 최종 동기화 확인\*\***

추가 Commit을 생성한 뒤 \`git push\`를 실행한 결과 새로운 Commit이 GitHub의 \`main\` Branch로 정상적으로 전송되었습니다.

이후 \`git status\`를 실행한 결과 다음 메시지가 표시되었습니다.

\`\`\`text

Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

\`\`\`

\`Your branch is up to date with 'origin/main'.\`은 로컬 \`main\` Branch와 GitHub의 \`origin/main\` Branch가 같은 Commit 상태라는 의미입니다.

\`nothing to commit, working tree clean\`은 현재 수정했지만 Commit하지 않은 파일이나 Git이 추적하지 않는 새 파일이 남아 있지 않다는 의미입니다.

이를 통해 다음 전체 흐름을 실제로 확인했습니다.

**\*\*변경사항 Staging → 문서화 Commit → 첫 \`git push -u origin main\` → 추적 관계 설정 → 새 증빙 파일 발견 → 다시 Commit → 이후 \`git push\`만으로 전송 → \`git status\`로 최종 Clean 상태 확인\*\***

특히 첫 Push 직후 증빙 이미지가 새로 생성되면서 다시 \`Untracked file\`이 발생했지만, 해당 파일을 다시 Staging하고 Commit한 뒤 Push하여 최종적으로 \`working tree clean\` 상태까지 만들었습니다.

이 과정은 Git에서 *\*\****\*\*새 파일 생성 → Staging → Commit → Push → 상태 확인\*\***\*\*이 반복적으로 이루어진다는 점을 실제 작업을 통해 확인한 사례입니다.

\`21-first-push-evidence-commit.jpg\`는 첫 Push 증빙 자료를 다시 Commit하는 중간 과정을 확인할 수 있는 참고 자료로 보관했으며, 최종 README에서는 중복을 줄이기 위해 별도의 본문 그림으로 사용하지 않았습니다.

**### 3.8 GitHub Repository 및 README 표시 확인**

로컬 Repository와 GitHub 원격 Repository의 동기화를 완료한 뒤, 실제 GitHub 웹페이지에서 Repository가 정상적으로 생성되었는지 확인했습니다.

또한 단순히 파일이 Push되었다는 것만 확인하지 않고, \`README.md\`가 GitHub 웹에서 실제 Markdown 문서로 정상 렌더링되는지와 README에 연결한 이미지가 올바르게 표시되는지도 직접 확인했습니다.

**#### 📷 GitHub Repository 및 README 전체 화면 확인**

![GitHub Repository 및 README 전체 화면]\(images/23-github-repository-and-readme-overview\.jpg)

**\*\*그림 18. GitHub Repository 생성 결과 및 README 표시 확인\*\***

GitHub 웹페이지에서 \`python-git-prompt-manager\` Repository가 정상적으로 생성되어 있는지 확인했습니다.

화면에서 다음 항목을 확인할 수 있습니다.

\- Repository 이름이 \`python-git-prompt-manager\`로 표시됨

\- Repository가 Public 상태로 생성됨

\- \`images/\` 폴더가 정상적으로 존재함

\- \`.gitignore\`, \`README.md\`, \`hello.py\`, \`main.py\` 파일이 표시됨

\- Commit 기록이 GitHub에 반영됨

\- Repository 첫 화면 아래에 \`README.md\` 내용이 실제 문서 형태로 표시됨

이를 통해 VS Code Terminal에서 생성하고 Push한 로컬 프로젝트가 GitHub Repository에 정상적으로 반영되었음을 확인했습니다.

**---**

**#### 📷 README Markdown 및 이미지 렌더링 확인**

![GitHub README 이미지 렌더링 확인]\(images/24-github-readme-image-rendering.jpg)

**\*\*그림 19. GitHub README Markdown 및 이미지 정상 표시 확인\*\***

GitHub Repository의 README 영역을 아래로 이동하여 Markdown 문법과 이미지가 실제 웹페이지에서 정상적으로 표시되는지 확인했습니다.

확인 결과 \`3.1 개발 도구 설치\`와 같은 Heading이 문서 제목 형태로 정상 렌더링되었으며, README에 작성한 Python 설치 증빙 이미지도 깨지지 않고 정상적으로 표시되었습니다.

이를 통해 단순히 Markdown 파일이 Repository에 존재하는 것뿐 아니라 다음 사항까지 확인했습니다.

**\*\*README 파일 업로드 → Markdown Heading 렌더링 → 이미지 경로 인식 → GitHub 웹에서 실제 이미지 표시\*\***

특히 로컬에서 작성한 이미지 경로가 GitHub에서도 정상적으로 동작한다는 것을 직접 확인함으로써, 제출자가 아닌 다른 사람이 Repository를 열었을 때도 README와 증빙 자료를 확인할 수 있는 상태임을 검증했습니다.

**---**

**## 4. 프로젝트 파일 구조**





현재 프로젝트는 다음과 같이 구성했습니다.

\`\`\`text

python-git-prompt-manager/

│

├── main.py

├── hello.py

├── README.md

├── .gitignore

│

└── images/

    ├── 01-development-environment.png

    ├── 02-python-installation.jpg

    ├── 03-vscode-installation.jpg

    ├── 04-git-installation.jpg

    ├── 05-git-add-status.png

    ├── 06-gitignore-desktop-ini.jpg

    ├── 07-gitignore-verification.jpg

    ├── 08-git-staging-final.jpg

    ├── 09-git-staging-complete.jpg

    ├── 10-before-first-commit.jpg

    ├── 11-first-commit-and-git-log.jpg

    ├── 12-github-cli-install-and-verification.jpg

    ├── 13-github-device-activation.jpg

    ├── 14-github-cli-authorization.jpg

    ├── 15-github-cli-confirm-access.jpg

    ├── 16-github-cli-login-success.jpg

    ├── 17-github-auth-status.jpg

    ├── 18-github-repository-and-remote.jpg

    ├── 19-github-setup-docs-commit.jpg

    ├── 20-first-github-push-and-status.jpg

    ├── 21-first-push-evidence-commit.jpg

    ├── 22-github-push-and-clean-status.jpg

    ├── 23-github-repository-and-readme-overview\.jpg

    ├── 24-github-readme-image-rendering.jpg

    ├── git-error-not-repository.jpg

    └── git-status-after-readme-update.jpg

\`\`\`

각 파일과 폴더의 역할은 다음과 같습니다.

\| 파일 및 폴더 | 역할 |

\|---|---|

\| \`main.py\` | 프롬프트 관리 프로그램의 주요 기능을 작성하는 Python 파일 |

\| \`hello.py\` | \`print("Hello")\`를 실행하여 Python이 정상적으로 동작하는지 확인하기 위한 파일 |

\| \`README.md\` | 프로젝트 소개, 개발 과정, 실행 방법 및 증빙 자료를 정리하는 문서 |

\| \`.gitignore\` | Git으로 관리할 필요가 없는 파일과 폴더를 추적 대상에서 제외하기 위한 설정 파일 |

\| \`images/\` | 설치 과정, 개발 환경, Git 작업 과정 및 프로그램 실행 결과 등의 증빙 이미지를 보관하는 폴더 |

프로그램 개발과 Git/GitHub 실습을 진행하면서 새로운 증빙 자료가 생성되면 \`images/\` 폴더에 순서대로 추가합니다.

**---**

**## 5. 프로그램 실행 방법**

VS Code에서 프로젝트 폴더를 연 뒤 Terminal(터미널)에서 다음 명령어를 입력합니다.

\`\`\`bash

python main.py

\`\`\`

\`python\`은 Python 프로그램을 실행한다는 뜻이고, \`main.py\`는 이번 과제에서 작성하는 프롬프트 관리 프로그램의 실행 파일입니다.

프로그램이 시작되면 메뉴 번호를 입력하여 원하는 기능을 선택합니다.





**## 6. 프로그램 주요 기능**

프로그램은 다음 필수 기능을 제공합니다.

기능    설명

프롬프트 추가   제목·내용·카테고리를 입력하여 새로운 프롬프트 등록

프롬프트 목록   저장된 모든 프롬프트 확인

카테고리별 조회 선택한 카테고리의 프롬프트만 확인

프롬프트 검색   제목 또는 내용에 검색어가 포함된 프롬프트 검색

상세 보기       선택한 프롬프트의 전체 내용 확인

즐겨찾기 관리   즐겨찾기 추가 또는 해제

즐겨찾기 목록   즐겨찾기된 프롬프트만 모아서 확인

종료    프로그램 종료

각 기능 수행 후 다시 메인 메뉴로 돌아오며, 잘못된 메뉴 번호를 입력하면 안내 메시지를 표시한 뒤 다시 입력할 수 있도록 구현합니다. 이는 과제의 메뉴 동작 요구사항입니다.

**## 7. 프로그램의 데이터 구조**

**### 7.1 List와 Dictionary**

List(리스트)는 여러 데이터를 순서대로 저장할 수 있는 Python 자료구조입니다.

Dictionary(딕셔너리)는 하나의 데이터에 포함된 여러 정보를 이름: 값 형태로 관리하는 자료구조입니다.

이번 프로그램에서는 여러 프롬프트를 하나의 List에 저장하고, 프롬프트 하나는 Dictionary로 표현합니다.

prompts (List)

│

├── 프롬프트 1 (Dictionary)

│   ├── title

│   ├── content

│   ├── category

│   └── favorite

│

├── 프롬프트 2 (Dictionary)

└── 프롬프트 3 (Dictionary)

예:

prompts = [

    {

        "title": "【실제 기본 프롬프트 제목】",

        "content": "【실제 프롬프트 내용】",

        "category": "【카테고리】",

        "favorite": False

    }

]

**### 왜 List + Dictionary를 선택했는가?**

여러 프롬프트를 순서대로 관리하기에는 List가 적합하고, 하나의 프롬프트에는 제목·내용·카테고리·즐겨찾기처럼 서로 다른 속성이 있으므로 Dictionary를 사용하면 각 정보의 의미를 명확하게 표현할 수 있습니다.

**### 한계**

데이터가 매우 많아지거나 프로그램 종료 후에도 계속 보존해야 하는 프로그램이라면 파일이나 데이터베이스와 같은 별도의 저장 방식이 필요합니다.

힌트: “사용했다”에서 끝내지 않고 무엇인지 → 왜 선택했는지 → 장점 → 한계까지 설명합니다.

과제에서도 List와 Dictionary를 사용하고 각 프롬프트에 제목·내용·카테고리·즐겨찾기 여부를 포함하도록 명시합니다.

**## 8. 기본 프롬프트 데이터**

프로그램 실행 시 이전 미션에서 작성한 프롬프트를 최소 3개 이상 기본 데이터로 제공합니다.

번호    제목    카테고리        출처

1       【직접 입력】   【직접 입력】   이전 미션

2       【직접 입력】   【직접 입력】   이전 미션

3       【직접 입력】   【직접 입력】   이전 미션

힌트: 여기에는 아무 예시를 새로 만드는 것이 아니라 사용자님이 실제 이전 미션에서 작성했던 프롬프트 최소 3개를 넣어야 합니다. 이 부분은 제가 임의로 결정하지 않겠습니다.

**## 9. 메뉴와 프로그램 흐름**

프로그램 실행

      ↓

메인 메뉴 출력

      ↓

사용자가 번호 입력

      ↓

선택한 기능 실행

      ↓

결과 출력

      ↓

메인 메뉴로 복귀

      ↓

0\. 종료 선택

      ↓

프로그램 종료

잘못된 메뉴 번호를 입력하면 프로그램이 종료되거나 오류가 발생하는 대신 안내 메시지를 출력하고 다시 메뉴를 보여줍니다.

📷 증빙

05-program-main-and-list.png

【이미지 삽입】

그림 5. 메인 메뉴 및 기본 프롬프트 목록

프로그램을 실행했을 때 메인 메뉴가 정상적으로 출력되고 기본 프롬프트가 최소 3개 이상 등록되어 있음을 확인한 화면입니다.

힌트: 메뉴 + 기본 데이터 + 목록 기능을 한 장에서 확인할 수 있도록 캡처하면 효율적입니다.

**## 10. 프롬프트 추가**

사용자는 다음 세 가지 정보를 입력하여 새로운 프롬프트를 등록할 수 있습니다.

제목

내용

카테고리

카테고리는 미리 정의된 목록에서 선택하거나 직접 입력할 수 있도록 구현합니다.

새로 등록된 프롬프트의 즐겨찾기 기본값은 False입니다. 과제에서도 입력값이 비어 있으면 다시 입력을 요구하고, 추가된 데이터는 프로그램 실행 중에만 유지하도록 명시합니다.

**### 입력 검증**

문제: 사용자가 제목이나 내용을 입력하지 않고 Enter를 누르면 내용이 없는 프롬프트가 등록될 수 있습니다.

해결: .strip()으로 앞뒤 공백을 제거한 뒤 입력값이 비어 있는지 검사하고, 비어 있으면 다시 입력하도록 합니다.

카테고리에서 직접 입력을 선택한 경우에도 빈 값을 입력하면 다시 입력하도록 합니다.

장점: 사용자의 단순한 입력 실수로 잘못된 데이터가 등록되는 것을 예방할 수 있습니다.

📷 증빙

06-add-prompt.png

【이미지 삽입】

그림 6. 프롬프트 추가 기능 테스트

제목·내용·카테고리를 입력해 새로운 프롬프트를 추가했으며, 이후 전체 목록의 개수가 3개 → 4개로 증가한 것을 통해 추가 기능이 정상적으로 동작함을 확인했습니다.

힌트: “추가되었습니다”만 캡처하지 말고 추가 결과가 실제 목록에 반영된 것까지 보여주세요.

**## 11. 프롬프트 목록 — Branch 활용 ★중요**

프롬프트 목록 기능은 과제에서 단순히 기능만 구현하는 것이 아니라, *\*\****\*\*\`main\`이 아닌 별도의 Branch에서 개발한 뒤 다시 \`main\` Branch에 Merge하는 과정까지 수행하도록 요구된 기능\*\***\*\*입니다.

따라서 목록 기능을 \`main\` Branch에서 바로 작성하지 않고, 먼저 전용 Branch를 생성한 뒤 해당 Branch에서 개발을 진행했습니다.

**### 11.1 프롬프트 목록 기능 개발용 Branch 생성**

Branch를 만들기 전에 프롬프트 추가 기능까지 \`main\` Branch에서 Commit하고 GitHub에 Push했습니다.

그 다음 프롬프트 목록 기능만 별도의 작업 공간에서 개발하기 위해 다음 명령어를 실행했습니다.

\`\`\`bash

git checkout -b feature/prompt-list

\`\`\`

\`git checkout -b\`는 새로운 Branch를 생성하는 동시에 해당 Branch로 이동하는 명령어입니다.

여기서:

\- \`feature\`는 새로운 기능을 개발하기 위한 Branch라는 의미입니다.

\- \`prompt-list\`는 이번 Branch에서 개발할 기능이 프롬프트 목록 기능이라는 의미입니다.

명령 실행 결과 다음 메시지가 표시되었습니다.

\`\`\`text

Switched to a new branch 'feature/prompt-list'

\`\`\`

Branch 생성 후 실제 현재 작업 Branch가 변경되었는지 다시 확인했습니다.

\`\`\`bash

git branch --show-current

\`\`\`

확인 결과:

\`\`\`text

feature/prompt-list

\`\`\`

가 출력되었습니다.

**#### 📷 프롬프트 목록 기능 개발용 Branch 생성 및 확인**

![feature/prompt-list Branch 생성 및 확인]\(images/20-feature-prompt-list-branch-created.jpg)

**\*\*그림 20. 프롬프트 목록 기능 개발용 \`feature/prompt-list\` Branch 생성 및 현재 Branch 확인\*\***

\`git checkout -b feature/prompt-list\`를 실행하여 새로운 Branch를 생성하면서 해당 Branch로 이동했습니다.

이후 \`git branch --show-current\`를 실행한 결과 현재 Branch가 \`feature/prompt-list\`로 표시되는 것을 확인했습니다.

VS Code 화면 왼쪽 아래의 Branch 표시 역시 \`feature/prompt-list\`로 변경되어 있어, 프롬프트 목록 기능을 \`main\`이 아닌 별도의 Branch에서 개발할 준비가 완료되었음을 확인했습니다.

이를 통해 다음 흐름을 실제로 검증했습니다.

**\*\*\`main\`에서 이전 기능 완료 → \`feature/prompt-list\` Branch 생성 → 새 Branch로 이동 → 현재 Branch 재확인\*\***

**---**

**### 11.2 프롬프트 목록 기능 구현 및 실행 확인**

\`feature/prompt-list\` Branch에서 프롬프트 목록 기능을 구현했습니다.

목록 기능은 등록된 각 프롬프트의 다음 정보를 한 줄에 표시하도록 구성했습니다.

\- 번호

\- 제목

\- 카테고리

\- 즐겨찾기 여부 \`★ / ☆\`

목록 출력을 위해 \`show\_prompt\_list()\` 함수를 작성했습니다.

\`\`\`python

def show\_prompt\_list():

    """등록된 프롬프트 목록을 번호, 제목, 카테고리, 즐겨찾기와 함께 출력한다."""

    print("\n=== 프롬프트 목록 ===")

    if not prompts:

        print("등록된 프롬프트가 없습니다.")

        return

    for index, prompt in enumerate(prompts, start=1):

        favorite\_mark = "★" if prompt["favorite"] else "☆"

        print(

            f"{index}. "

            f"{favorite\_mark} "

            f"{prompt['title']} "

            f"[{prompt['category']}]"

        )

\`\`\`

여기서 다음 부분은 프롬프트가 하나도 없을 때를 처리합니다.

\`\`\`python

if not prompts:

    print("등록된 프롬프트가 없습니다.")

    return

\`\`\`

이 코드는 *\*\****\*\*반드시 \`show\_prompt\_list()\` 함수 내부에 있어야 합니다.\*\***\*\*

현재 실제 \`main.py\`에서는 이 코드가 함수 내부에 있으며, 프로그램도 정상 실행되었습니다. 만약 이 코드가 파일 맨 아래 함수 밖에 별도로 존재한다면 삭제해야 합니다.

목록 번호는 다음 코드로 \`1\`부터 표시합니다.

\`\`\`python

enumerate(prompts, start=1)

\`\`\`

\`enumerate()\`는 List의 각 항목을 순서대로 처리하면서 번호도 함께 사용할 수 있도록 해주는 Python 기능입니다.

또한 각 프롬프트의 \`favorite\` 값에 따라 즐겨찾기를 다음처럼 표시합니다.

\`\`\`text

True  → ★

False → ☆

\`\`\`

현재 기본 프롬프트의 \`favorite\` 값은 모두 \`False\`이므로 최초 목록에서는 \`☆\`가 표시됩니다.

기능 구현 후 현재 Branch가 여전히 \`feature/prompt-list\`인지 확인했습니다.

\`\`\`bash

git branch --show-current

\`\`\`

확인 결과:

\`\`\`text

feature/prompt-list

\`\`\`

가 출력되었습니다.

그 다음 프로그램을 실행했습니다.

\`\`\`bash

python .\main.py

\`\`\`

메인 메뉴에서 \`2. 프롬프트 목록\`을 선택한 결과 다음과 같이 기본 프롬프트 4개가 정상적으로 출력되었습니다.

\`\`\`text

\\=== 프롬프트 목록 ===

1\. ☆ 몸 이상 신호 기반 컬러푸드 서비스 기획 [텍스트 생성]

2\. ☆ 주식투자 위험 영상 이미지 수정 [이미지 생성]

3\. ☆ 결과 캐싱 개념 설명 [텍스트 생성]

4\. ☆ 복수 여행지 증빙 확인 [기타]

\`\`\`

목록 출력이 끝난 뒤 프로그램이 종료되지 않고 다시 메인 메뉴로 돌아오는 것도 확인했습니다.

**#### 📷 \`feature/prompt-list\` Branch에서 프롬프트 목록 실행 확인**

![feature/prompt-list Branch 프롬프트 목록 실행]\(images/21-feature-prompt-list-display.jpg)

**\*\*그림 21. \`feature/prompt-list\` Branch에서 프롬프트 목록 기능 실행 확인\*\***

화면 상단에서 \`git branch --show-current\` 명령 결과가 \`feature/prompt-list\`로 표시되는 것을 확인했습니다.

같은 화면에서 Python 프로그램을 실행한 뒤 \`2\`번 메뉴를 선택하여 번호, 제목, 카테고리, 즐겨찾기 표시가 포함된 프롬프트 목록이 정상적으로 출력되는 것도 확인했습니다.

또한 목록 출력 후 메인 메뉴가 다시 표시되어, 기능 실행 후 프로그램이 정상적으로 메인 메뉴로 복귀하는 것도 확인했습니다.

이를 통해 단순히 목록 기능이 동작한다는 것뿐 아니라, *\*\****\*\*해당 기능을 실제로 \`feature/prompt-list\` Branch에서 개발하고 테스트했다는 사실까지 함께 검증했습니다.\*\***\*\*

확인한 흐름은 다음과 같습니다.

**\*\*\`feature/prompt-list\` Branch 확인 → 프로그램 실행 → 2번 목록 선택 → 기본 프롬프트 4개 출력 → 메인 메뉴 복귀\*\***

**---**

**### 11.3 Branch에서 기능 Commit 후 \`main\`에 Merge**

프롬프트 목록 기능 구현과 실행 테스트를 완료한 뒤, 현재 작업 중인 \`feature/prompt-list\` Branch에서 변경사항을 Commit했습니다.

먼저 변경된 파일을 Staging Area에 등록하고 상태를 확인했습니다.

\`\`\`bash

git add .

git status

\`\`\`

\`git status\`를 통해 현재 Branch가 \`feature/prompt-list\`인지 확인하고, \`main.py\`, \`README.md\`와 이번 작업에서 생성한 증빙 이미지가 Commit 대상으로 등록된 것도 확인했습니다.

이후 다음 명령어로 프롬프트 목록 기능을 Commit했습니다.

\`\`\`bash

git commit -m "feat: add prompt list"

\`\`\`

Commit 결과 다음과 같이 \`feature/prompt-list\` Branch에 새로운 변경 이력이 생성되었습니다.

\`\`\`text

[feature/prompt-list cb56cde] feat: add prompt list

\`\`\`

**#### 📷 \`feature/prompt-list\` Branch에서 목록 기능 Commit**

![프롬프트 목록 기능 Branch Commit]\(images/31-feature-prompt-list-commit.jpg)

**\*\*그림 22. \`feature/prompt-list\` Branch에서 프롬프트 목록 기능 Commit\*\***

화면에서 현재 Branch가 \`feature/prompt-list\`인 상태에서 \`git add .\`, \`git status\`, \`git commit -m "feat: add prompt list"\`를 순서대로 실행한 것을 확인할 수 있습니다.

이를 통해 프롬프트 목록 기능이 \`main\` Branch에서 바로 Commit된 것이 아니라, 과제 요구사항에 따라 별도의 \`feature/prompt-list\` Branch에서 개발되고 Commit되었다는 변경 이력을 남겼습니다.

**---**

Branch Commit을 완료한 뒤 작업 폴더에 남아 있는 변경사항이 없는지 확인했습니다.

\`\`\`bash

git status

\`\`\`

확인 결과:

\`\`\`text

On branch feature/prompt-list

nothing to commit, working tree clean

\`\`\`

이 표시되어 목록 기능 관련 변경사항이 모두 Commit된 상태임을 확인했습니다.

그 다음 \`main\` Branch로 이동했습니다.

\`\`\`bash

git checkout main

\`\`\`

실행 결과:

\`\`\`text

Switched to branch 'main'

\`\`\`

이 표시되어 현재 작업 Branch가 \`feature/prompt-list\`에서 \`main\`으로 변경되었습니다.

이후 다음 명령어를 사용하여 \`feature/prompt-list\`에서 개발한 목록 기능을 \`main\` Branch에 병합했습니다.

\`\`\`bash

git merge feature/prompt-list

\`\`\`

Merge 결과 다음과 같이 \`Fast-forward\`가 표시되었습니다.

\`\`\`text

Fast-forward

\`\`\`

\`Fast-forward\`는 Merge 실패나 오류가 아니라, \`main\` Branch 이후에 별도의 충돌되는 Commit이 없었기 때문에 \`main\`이 \`feature/prompt-list\`의 최신 Commit 위치까지 그대로 이동하여 병합된 것을 의미합니다.

**#### 📷 \`feature/prompt-list\` Branch를 \`main\`에 Merge**

![프롬프트 목록 Branch를 main에 Merge]\(images/32-feature-prompt-list-merge-to-main.jpg)

**\*\*그림 23. \`feature/prompt-list\` Branch Commit 후 \`main\` Checkout 및 Merge\*\***

화면에서 다음 과정을 연속으로 확인할 수 있습니다.

\- \`feature/prompt-list\` Branch의 작업 상태가 Clean인지 확인

\- \`git checkout main\`으로 \`main\` Branch 이동

\- \`git merge feature/prompt-list\` 실행

\- \`Fast-forward\` 방식으로 Merge 완료

\- \`main.py\`, \`README.md\` 및 증빙 이미지가 \`main\`에 반영됨

이를 통해 과제에서 요구한 다음 개발 흐름을 실제로 수행했습니다.

**\*\*\`feature/prompt-list\` 생성 → 목록 기능 개발 및 테스트 → Branch에서 Commit → \`main\` Checkout → \`feature/prompt-list\` Merge\*\***

즉, 프롬프트 목록 기능을 \`main\`에서 직접 개발한 것이 아니라 별도의 Branch에서 독립적으로 개발한 뒤 다시 \`main\`에 합치는 Git Branch 작업 과정을 완료했습니다.





**### 11.4 Git Log를 통한 Branch 및 Merge 기록 확인**

\`feature/prompt-list\` Branch의 프롬프트 목록 기능을 \`main\` Branch에 Merge한 뒤, Git 변경 이력에서도 정상적으로 반영되었는지 확인했습니다.

다음 명령어를 실행했습니다.

\`\`\`bash

git log --oneline --graph --all --decorate

\`\`\`

각 옵션의 의미는 다음과 같습니다.

\| 옵션 | 의미 |

\|---|---|

\| \`--oneline\` | 각 Commit을 한 줄로 간단하게 표시 |

\| \`--graph\` | Commit과 Branch 관계를 그래프 형태로 표시 |

\| \`--all\` | 현재 Branch뿐 아니라 다른 Branch의 기록도 함께 표시 |

\| \`--decorate\` | \`HEAD\`, \`main\`, \`feature/prompt-list\`, \`origin/main\`과 같은 Branch 위치를 함께 표시 |

**#### 📷 Git Log를 통한 Branch 및 Merge 기록 확인**

![프롬프트 목록 Branch Git Log 확인]\(images/33-feature-prompt-list-git-log.jpg)

**\*\*그림 24. \`git log --oneline --graph --all --decorate\`를 통한 Branch 및 Merge 기록 확인\*\***

Git Log의 최신 Commit에서 다음과 같은 내용을 확인했습니다.

\`\`\`text

cb56cde (HEAD -> main, feature/prompt-list) feat: add prompt list

\`\`\`

\`HEAD -> main\`은 현재 작업 위치가 \`main\` Branch라는 의미입니다.

같은 Commit에 \`feature/prompt-list\`도 함께 표시되어 있어, 프롬프트 목록 기능을 개발한 Branch와 \`main\` Branch가 Merge 후 동일한 최신 Commit을 가리키고 있음을 확인했습니다.

또한 당시 \`origin/main\`은 다음 이전 Commit을 가리키고 있었습니다.

\`\`\`text

45c6f11 (origin/main) feat: add prompt creation

\`\`\`

이는 로컬 \`main\`에는 프롬프트 목록 기능 Merge가 완료되었지만, 아직 해당 최신 Commit을 GitHub 원격 Repository에는 Push하지 않은 상태라는 의미입니다.

이번 Merge는 \`Fast-forward\` 방식으로 이루어졌기 때문에 Git Graph가 별도의 가지가 갈라졌다 다시 합쳐지는 모양으로 표시되지는 않았습니다.

\`Fast-forward\` Merge에서는 \`main\` Branch가 \`feature/prompt-list\`의 최신 Commit 위치까지 앞으로 이동하므로, Merge 후 두 Branch가 같은 Commit을 가리키는 것이 정상입니다.

이를 통해 다음 과정을 Git 명령 실행 결과뿐 아니라 실제 Commit 기록에서도 다시 검증했습니다.

**\*\*Branch 생성 → 목록 기능 개발 → Branch Commit → \`main\` Checkout → Fast-forward Merge → Git Log를 통한 Branch 위치 및 Commit 기록 확인\*\***

**---**



**### 11.5 Merge 결과 GitHub Push 및 최종 동기화 확인**

프롬프트 목록 기능의 Branch 개발, Commit, \`main\` Merge, Git Log 검증까지 완료한 뒤 관련 README와 증빙 자료를 Git 변경 이력에 추가했습니다.

먼저 변경된 파일을 Staging Area에 등록하고 상태를 확인했습니다.

\`\`\`bash

git add .

git status

\`\`\`

이후 다음 Commit을 생성했습니다.

\`\`\`bash

git commit -m "docs: add prompt list merge evidence"

\`\`\`

**#### 📷 프롬프트 목록 Merge 증빙 문서화 Commit**

![프롬프트 목록 Merge 증빙 Commit]\(images/34-prompt-list-merge-evidence-commit.jpg)

**\*\*그림 25. 프롬프트 목록 Branch·Merge 증빙 자료 문서화 Commit\*\***

\`README.md\`와 \`31-feature-prompt-list-commit.jpg\`, \`32-feature-prompt-list-merge-to-main.jpg\`, \`33-feature-prompt-list-git-log.jpg\`를 Staging한 뒤 \`docs: add prompt list merge evidence\`라는 메시지로 Commit했습니다.

이를 통해 Branch 생성·기능 개발·Merge·Git Log 확인 과정에서 생성된 증빙 자료도 Git 변경 이력으로 관리했습니다.

Commit 후 다음 명령어를 실행하여 GitHub 원격 Repository에 최신 변경사항을 전송했습니다.

\`\`\`bash

git push

\`\`\`

Push가 완료된 뒤 최종 동기화 상태를 확인했습니다.

\`\`\`bash

git status

\`\`\`

확인 결과 다음 메시지가 표시되었습니다.

\`\`\`text

Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

\`\`\`

**#### 📷 프롬프트 목록 Merge 결과 Push 및 최종 Clean 상태 확인**

![프롬프트 목록 Merge Push 및 Clean 상태]\(images/35-prompt-list-merge-push-and-clean-status.jpg)

**\*\*그림 26. 프롬프트 목록 Branch 작업의 GitHub Push 및 최종 동기화 확인\*\***

\`git push\` 실행 결과 최신 Commit이 GitHub의 \`main\` Branch로 정상적으로 전송되었습니다.

이후 \`git status\`에서 로컬 \`main\` Branch와 GitHub의 \`origin/main\` Branch가 같은 상태임을 확인했으며, \`nothing to commit, working tree clean\` 메시지를 통해 처리되지 않은 변경사항이나 새 파일이 남아 있지 않은 것도 확인했습니다.

이를 통해 프롬프트 목록 기능에 대한 전체 Git 작업 흐름을 완료했습니다.

**\*\*Branch 생성 → 기능 개발 → Branch Commit → \`main\` Merge → Git Log 검증 → 증빙 문서화 Commit → GitHub Push → 최종 Clean 상태 확인\*\***

**---**

## 12. 카테고리별 조회

프롬프트를 모두 한 번에 확인하는 것뿐 아니라 원하는 카테고리의 프롬프트만 골라 확인할 수 있도록 카테고리별 조회 기능을 구현했습니다.

메인 메뉴의 다음 항목을 선택하면 사용할 수 있습니다.

```text
3. 카테고리별 조회
```

카테고리별 조회 기능은 다음 흐름으로 동작합니다.

**카테고리 목록 표시 → 카테고리 번호 선택 → 해당 카테고리 프롬프트 검색 → 결과 출력 → 메인 메뉴 복귀**

---

### 12.1 카테고리 목록 구성

프롬프트 추가 기능에서는 사용자가 미리 정의된 카테고리를 선택할 수도 있고 `0. 직접 입력`을 이용해 새로운 카테고리를 입력할 수도 있습니다.

따라서 카테고리별 조회에서도 기본 카테고리만 보여주는 것이 아니라, 실제 프롬프트에 사용된 사용자 정의 카테고리까지 조회할 수 있도록 구성했습니다.

이를 위해 다음 함수를 작성했습니다.

```python
def get_available_categories():
    """기본 카테고리와 사용자가 직접 추가한 카테고리를 함께 반환한다."""
    categories = CATEGORIES.copy()

    for prompt in prompts:
        category = prompt["category"]

        if category not in categories:
            categories.append(category)

    return categories
```

먼저 `CATEGORIES.copy()`를 사용해 기본 카테고리 목록을 복사합니다.

그 다음 등록된 프롬프트의 `category` 값을 확인하여 기존 목록에 없는 카테고리가 있으면 추가합니다.

이 방식을 사용하면 프롬프트 추가 과정에서 사용자가 직접 만든 카테고리도 이후 카테고리별 조회 기능에서 다시 선택할 수 있습니다.

또한 `CATEGORIES` 자체를 직접 수정하지 않고 복사본을 사용하므로 프로그램의 기본 카테고리 목록은 그대로 유지됩니다.

---

### 12.2 조회할 카테고리 선택

조회할 카테고리를 번호로 선택할 수 있도록 다음 함수를 작성했습니다.

```python
def select_category_for_filter():
    """카테고리별 조회에 사용할 카테고리를 선택한다."""
    categories = get_available_categories()

    print("\n조회할 카테고리를 선택하세요.")

    for index, category in enumerate(categories, start=1):
        print(f"{index}. {category}")

    while True:
        try:
            choice = input("선택: ").strip()
        except (EOFError, KeyboardInterrupt):
            return None

        if choice.isdigit():
            number = int(choice)

            if 1 <= number <= len(categories):
                return categories[number - 1]

        print("잘못된 카테고리 번호입니다. 다시 입력해주세요.")
```

`enumerate(categories, start=1)`을 사용하여 각 카테고리에 `1`부터 번호를 부여했습니다.

사용자가 숫자가 아닌 값을 입력하거나 실제 카테고리 목록의 범위를 벗어난 번호를 입력하면 다음 메시지를 출력합니다.

```text
잘못된 카테고리 번호입니다. 다시 입력해주세요.
```

잘못된 입력이 들어와도 프로그램을 종료하지 않고 `while` 반복문을 통해 다시 번호를 입력할 수 있도록 했습니다.

실제 테스트에서는 존재하지 않는 번호인 `9`를 입력했고, 안내 메시지가 표시된 뒤 정상 카테고리 번호를 다시 입력할 수 있음을 확인했습니다.

---

### 12.3 선택한 카테고리의 프롬프트 필터링

선택한 카테고리의 프롬프트만 골라내는 작업은 `show_prompts_by_category()` 함수에서 수행합니다.

```python
def show_prompts_by_category():
    """선택한 카테고리에 해당하는 프롬프트만 출력한다."""
    category = select_category_for_filter()

    if category is None:
        print("\n카테고리별 조회를 취소합니다.")
        return

    filtered_prompts = [
        prompt
        for prompt in prompts
        if prompt["category"] == category
    ]

    print(f"\n=== {category} 카테고리 ===")

    if not filtered_prompts:
        print("해당 카테고리에 등록된 프롬프트가 없습니다.")
        return

    for index, prompt in enumerate(filtered_prompts, start=1):
        favorite_mark = "★" if prompt["favorite"] else "☆"

        print(
            f"{index}. "
            f"{favorite_mark} "
            f"{prompt['title']}"
        )
```

다음 부분에서 전체 `prompts` List를 확인하고, 선택한 카테고리와 같은 프롬프트만 새로운 List에 저장합니다.

```python
filtered_prompts = [
    prompt
    for prompt in prompts
    if prompt["category"] == category
]
```

예를 들어 `텍스트 생성`을 선택하면 전체 프롬프트 가운데 다음 조건을 만족하는 항목만 남습니다.

```python
prompt["category"] == "텍스트 생성"
```

이처럼 여러 데이터 가운데 조건에 맞는 데이터만 골라내는 작업을 **필터링(Filter)**이라고 합니다.

---

### 12.4 출력 중복을 줄인 이유

전체 프롬프트 목록에서는 서로 다른 카테고리의 프롬프트가 함께 표시되기 때문에 각 항목에 카테고리를 같이 표시합니다.

예:

```text
1. ☆ 몸 이상 신호 기반 컬러푸드 서비스 기획 [텍스트 생성]
2. ☆ 주식투자 위험 영상 이미지 수정 [이미지 생성]
```

반면 카테고리별 조회에서는 화면의 제목에서 이미 선택한 카테고리를 확인할 수 있습니다.

예:

```text
=== 텍스트 생성 카테고리 ===
```

따라서 각 프롬프트 뒤에 `[텍스트 생성]`을 다시 반복해서 표시하지 않고 다음처럼 간결하게 출력했습니다.

```text
1. ☆ 몸 이상 신호 기반 컬러푸드 서비스 기획
2. ☆ 결과 캐싱 개념 설명
```

전체 목록에서는 카테고리 구분이 필요하지만, 카테고리별 조회에서는 이미 같은 종류의 프롬프트만 출력되므로 중복 정보를 줄이는 편이 더 읽기 쉽다고 판단했습니다.

---

### 12.5 조회 결과가 없는 경우 처리

선택한 카테고리에 등록된 프롬프트가 하나도 없을 수도 있습니다.

이 경우 빈 화면만 보여주는 대신 다음 조건으로 안내 메시지를 출력하도록 구현했습니다.

```python
if not filtered_prompts:
    print("해당 카테고리에 등록된 프롬프트가 없습니다.")
    return
```

조회 결과가 없으면 다음과 같이 표시됩니다.

```text
해당 카테고리에 등록된 프롬프트가 없습니다.
```

현재 기본 프롬프트에는 `페르소나` 카테고리의 데이터가 없으므로 실제 실행 테스트에서 `페르소나`를 선택하여 빈 결과 처리 기능을 검증했습니다.

빈 결과가 발생해도 오류로 종료되지 않고 안내 메시지를 출력한 뒤 다시 메인 메뉴로 돌아가도록 구성했습니다.

---

### 12.6 메인 메뉴 연결

메인 메뉴에서 `3`번을 선택하면 카테고리별 조회 기능이 실행되도록 연결했습니다.

```python
elif choice == "3":
    show_prompts_by_category()
```

카테고리별 조회 함수의 실행이 끝나면 `main()` 함수의 `while` 반복문이 계속 실행되므로 프로그램이 종료되지 않고 다시 메인 메뉴가 표시됩니다.

따라서 별도의 “메뉴로 돌아가기” 코드를 반복해서 작성하지 않아도 각 기능 수행 후 메인 메뉴로 자연스럽게 복귀합니다.

---

### 12.7 실제 실행 테스트

구현한 카테고리별 조회 기능을 다음 명령어로 실행하여 테스트했습니다.

```bash
python .\main.py
```

이번 테스트에서는 정상적인 결과만 확인하지 않고 다음 두 상황을 함께 검증했습니다.

1. 잘못된 카테고리 번호를 입력했을 때 다시 입력할 수 있는지
2. 선택한 카테고리에 프롬프트가 없을 때 안내 메시지가 정상적으로 표시되는지

---

#### 테스트 1 — 잘못된 번호 처리 후 정상 카테고리 조회

먼저 메인 메뉴에서 `3. 카테고리별 조회`를 선택했습니다.

카테고리 선택 화면에서 실제 선택 범위를 벗어난 번호인 `9`를 입력했습니다.

```text
선택: 9
```

그 결과 다음 안내 메시지가 표시되었습니다.

```text
잘못된 카테고리 번호입니다. 다시 입력해주세요.
```

프로그램은 종료되지 않았으며 다시 카테고리 번호 입력을 기다렸습니다.

이어서 `1. 텍스트 생성`을 선택했습니다.

```text
선택: 1
```

실제 실행 결과 다음 두 개의 프롬프트만 출력되었습니다.

```text
=== 텍스트 생성 카테고리 ===
1. ☆ 몸 이상 신호 기반 컬러푸드 서비스 기획
2. ☆ 결과 캐싱 개념 설명
```

기본 프롬프트 4개 가운데 `텍스트 생성` 카테고리에 해당하는 2개만 정확하게 필터링된 것을 확인했습니다.

또한 출력이 끝난 뒤 프로그램이 종료되지 않고 메인 메뉴가 다시 표시되는 것도 확인했습니다.

#### 📷 잘못된 카테고리 번호 처리 및 정상 조회 결과

![카테고리별 조회 잘못된 번호 처리 및 정상 결과](images/36-category-filter-invalid-input-and-results.jpg)

**그림 27. 잘못된 카테고리 번호 재입력 및 텍스트 생성 카테고리 조회 결과**

위 화면에서는 다음 과정을 한 번에 확인할 수 있습니다.

- 메인 메뉴에서 `3. 카테고리별 조회` 선택
- 존재하지 않는 카테고리 번호 `9` 입력
- `잘못된 카테고리 번호입니다. 다시 입력해주세요.` 안내 출력
- 정상 번호 `1` 재입력
- `텍스트 생성` 카테고리에 해당하는 프롬프트 2개만 출력
- 기능 수행 후 메인 메뉴로 복귀

이를 통해 **잘못된 입력 검증과 정상적인 카테고리 필터링이 모두 작동하는 것**을 확인했습니다.

---

#### 테스트 2 — 조회 결과가 없는 카테고리 처리

첫 번째 조회가 끝나고 메인 메뉴가 다시 표시된 뒤 다시 `3. 카테고리별 조회`를 선택했습니다.

이번에는 기본 프롬프트가 등록되어 있지 않은 `4. 페르소나`를 선택했습니다.

실제 실행 결과 다음과 같이 표시되었습니다.

```text
=== 페르소나 카테고리 ===
해당 카테고리에 등록된 프롬프트가 없습니다.
```

이후 프로그램이 종료되거나 오류가 발생하지 않고 다시 메인 메뉴가 표시되었습니다.

빈 결과 처리 과정은 한 장의 화면에 전체 흐름이 모두 들어가지 않아 두 장의 연속된 증빙 화면으로 확인했습니다.

#### 📷 조회 결과가 없는 카테고리 처리

![빈 카테고리 선택 과정](<images/37-category-filter-empty-result (01).jpg>)

![빈 카테고리 결과 및 메뉴 복귀](<images/38-category-filter-empty-result (02).jpg>)

**그림 28. 페르소나 카테고리의 빈 조회 결과 처리 및 메인 메뉴 복귀**

그림 28의 두 화면은 하나의 연속된 실행 과정을 나누어 보여줍니다.

`37-category-filter-empty-result (01).jpg`에서는 메인 메뉴에서 카테고리별 조회를 다시 선택하고 `4. 페르소나`를 선택하는 과정까지 확인할 수 있습니다.

`38-category-filter-empty-result (02).jpg`에서는 선택한 `페르소나` 카테고리에 등록된 프롬프트가 없어 다음 메시지가 표시되는 것을 확인할 수 있습니다.

```text
해당 카테고리에 등록된 프롬프트가 없습니다.
```

또한 안내 메시지를 출력한 뒤 다시 메인 메뉴가 표시되어 빈 조회 결과에서도 프로그램이 정상적으로 계속 실행되는 것을 확인했습니다.

이를 통해 **카테고리 선택 → 데이터 검색 → 빈 결과 판단 → 사용자 안내 → 메인 메뉴 복귀** 흐름이 정상적으로 동작하는 것을 검증했습니다.

---

### 12.8 구현 결과 정리

이번 카테고리별 조회 기능에서는 다음 항목을 실제 실행으로 확인했습니다.

| 확인 항목 | 결과 |
|---|---|
| 기본 카테고리 목록 표시 | ✅ 정상 |
| 카테고리 번호 선택 | ✅ 정상 |
| 잘못된 번호 재입력 | ✅ 정상 |
| 선택한 카테고리만 필터링 | ✅ 정상 |
| 즐겨찾기 `★ / ☆` 표시 | ✅ 정상 |
| 사용자 정의 카테고리도 조회 목록에 포함 가능한 구조 | ✅ 구현 |
| 조회 결과 없음 안내 | ✅ 정상 |
| 기능 실행 후 메인 메뉴 복귀 | ✅ 정상 |

특히 정상적인 조회 결과만 확인하는 데서 끝내지 않고 **잘못된 입력과 빈 조회 결과까지 함께 테스트**하여 예외 상황에서도 프로그램이 중단되지 않는 것을 확인했습니다.

카테고리별 조회 기능은 별도의 외부 Library 없이 Python의 List, 반복문, 조건문, List Comprehension을 이용하여 구현했습니다.

이를 통해 다음 전체 흐름을 실제로 확인했습니다.

**메인 메뉴 → 카테고리 목록 → 잘못된 입력 처리 → 정상 카테고리 선택 → 조건에 맞는 프롬프트 필터링 → 빈 결과 처리 → 메인 메뉴 복귀**

---

**## 13. 프롬프트 검색**

사용자가 입력한 키워드가 제목 또는 내용에 포함되어 있는 프롬프트를 검색합니다. 검색 결과가 없으면 별도의 안내 메시지를 출력합니다. 이는 과제의 필수 검색 요구사항입니다.

추가하기 좋은 검색 개선

필수 요구사항을 변경하지 않는 범위에서 다음을 적용하는 것을 권장합니다.

지원 기능

제목 부분 일치

내용 부분 일치

영문 대소문자 무시

예를 들어 lower()를 사용하면 Python, PYTHON, python을 같은 검색어처럼 처리할 수 있습니다.

현재 검색의 한계

오타 자동 수정, 띄어쓰기 자동 보정, 특수문자 정규화, 정규식 검색은 지원하지 않습니다.

힌트: 구현한 기능뿐 아니라 무엇까지 되고 무엇은 안 되는지 설명하면 프로그램을 더 정확하게 이해할 수 있습니다.

📷 증빙

08-search-result.png

【이미지 삽입】

그림 8. 제목 및 내용 키워드 검색 테스트

검색어 【실제 검색어】를 입력한 결과 제목 또는 내용에 해당 검색어가 포함된 프롬프트가 출력되는 것을 확인했습니다.

**## 14. 프롬프트 상세 보기**

사용자가 프롬프트 번호를 입력하면 다음 정보를 모두 보여줍니다.

제목

카테고리

즐겨찾기 여부

전체 내용

잘못된 번호를 입력하면 오류로 종료하지 않고 안내 메시지를 출력합니다.

📷 증빙

09-prompt-detail.png

【이미지 삽입】

그림 9. 프롬프트 상세 보기

프롬프트 번호를 선택했을 때 제목·카테고리·즐겨찾기 여부와 전체 내용이 정상적으로 출력되는 것을 확인했습니다.

**## 15. 즐겨찾기**

즐겨찾기 여부에는 Python의 Boolean(불리언) 값을 사용합니다.

True  = 즐겨찾기

False = 일반

Boolean은 True 또는 False처럼 두 가지 상태를 표현하는 자료형입니다.

사용자는 프롬프트 번호를 입력하여 즐겨찾기를 추가하거나 해제할 수 있으며, 즐겨찾기된 프롬프트만 별도로 모아서 확인할 수도 있습니다.

📷 증빙

10-favorites.png

【이미지 삽입】

그림 10. 즐겨찾기 추가·해제 및 목록 확인

프롬프트의 즐겨찾기 상태를 변경한 뒤 즐겨찾기 목록에서 실제로 변경 결과가 반영되었음을 확인했습니다.

힌트: 기능 수행 → 결과 확인이 한 화면 또는 연속 화면에서 드러나도록 합니다.

**## 16. 함수 분리와 코드 구조**

함수(Function)란 특정 작업을 수행하는 코드를 하나의 이름으로 묶은 것입니다.

모든 코드를 한곳에 작성하지 않고 기능별로 함수를 나눕니다.

예:

show\_menu()        → 메뉴 출력

add\_prompt()       → 프롬프트 추가

show\_list()        → 전체 목록

show\_by\_category() → 카테고리별 조회

search\_prompt()    → 검색

show\_detail()      → 상세 보기

manage\_favorite()  → 즐겨찾기 추가/해제

show\_favorites()   → 즐겨찾기 목록

왜 함수를 나누었는가?

각 코드의 역할을 쉽게 파악할 수 있고 문제가 발생했을 때 수정할 위치를 찾기 쉬우며, 같은 기능을 필요할 때 다시 사용할 수 있기 때문입니다.

과제에서도 모든 코드를 한 함수에 몰아넣지 않고 기능별로 분리하도록 명시합니다.

힌트: 최종 코드에서 실제 사용한 함수 이름으로 바꿉니다.

**## 17. 조건문과 반복문**

**### 조건문**

if / elif / else는 사용자의 선택에 따라 서로 다른 기능을 실행하기 위해 사용합니다.

예:

1 입력 → 프롬프트 추가

2 입력 → 프롬프트 목록

3 입력 → 카테고리별 조회

...

0 입력 → 종료

**### 반복문**

while은 사용자가 종료를 선택할 때까지 메뉴를 계속 표시하기 위해 사용합니다.

힌트: 코드를 줄마다 설명하기보다 “이 문법이 프로그램에서 무슨 일을 하는가?”를 설명하면 초보자가 이해하기 쉽습니다.

**## 18. 프로그램 실행 중 데이터 유지와 종료 시 초기화 ★중요**

프로그램 실행 중 새로 추가한 프롬프트와 즐겨찾기 상태는 유지됩니다.

하지만 프로그램을 종료한 뒤 다시 실행하면 처음 준비된 기본 데이터 상태로 돌아갑니다.

프로그램 시작

   ↓

기본 프롬프트 3개

   ↓

새 프롬프트 추가

   ↓

실행 중에는 유지

   ↓

프로그램 종료

   ↓

다시 실행

   ↓

기본 상태로 초기화

이것은 오류가 아니라 필수 과제에서 요구한 정상 동작입니다. 최종 결과물 설명에도 실행 중에는 상태가 유지되고 종료 시 초기화된다고 명시되어 있습니다.

힌트: 보너스 JSON을 구현하더라도 이 필수 동작을 무심코 바꾸지 않도록 주의합니다.

**## 19. Git과 GitHub**

**### Git을 사용하는 이유**

Git은 코드의 변경 이력을 기록하여 언제 어떤 기능을 추가하거나 수정했는지 확인할 수 있게 해주는 도구입니다.

이번 과제에서는 기능 하나를 완성할 때마다 의미 있는 Commit을 남깁니다.

**### 주요 Git 명령어**

명령어  초보자용 설명

git init        현재 폴더를 Git으로 관리하기 시작

git add 다음 Commit에 포함할 변경사항 선택

git commit      현재 변경사항을 하나의 기록으로 저장

git push        내 PC의 Git 기록을 GitHub로 전송

git pull        GitHub의 최신 변경사항을 내 PC로 가져옴

git checkout    작업할 Branch로 이동

git clone       GitHub 저장소 전체를 내 PC로 복사

git merge       다른 Branch에서 작업한 내용을 현재 Branch에 합침

과제에서는 이 8개 명령을 각각 최소 1회 이상 사용해야 합니다.

**## 20. Git 작업 과정**

GitHub Repository 생성

        ↓

로컬 프로젝트 폴더 생성

        ↓

git init

        ↓

.gitignore / README.md 생성

        ↓

git add

        ↓

git commit

        ↓

원격 Repository 연결

        ↓

git push

        ↓

기능별 개발 + Commit

        ↓

feature/prompt-list 생성

        ↓

목록 기능 개발 + Commit

        ↓

checkout main

        ↓

merge feature/prompt-list

        ↓

push

힌트: 실제 수행한 순서와 명령을 최종적으로 맞춰 수정합니다.

**## 21. 의미 있는 Commit 기록**

과제에서는 최소 10개 이상의 의미 있는 기능 단위 Commit을 요구합니다.

권장 예시는 다음과 같습니다.

chore: initialize Python project

feat: add default prompt data

feat: add main menu

feat: add prompt creation

feat: add prompt list

feat: add category filter

feat: add prompt search

feat: add prompt detail view

feat: add favorite toggle

feat: add favorite list

fix: validate empty prompt input

docs: add README usage guide

힌트: 실제로 그 작업을 한 시점에 Commit해야 합니다. 나중에 개수만 맞추기 위한 빈 Commit은 사용하지 않습니다.

📷 증빙

04-git-log-graph.png

【이미지 삽입】

그림 4. Git Commit 및 Branch 병합 기록

Git Graph를 통해 10개 이상의 기능 단위 Commit과 feature/prompt-list Branch의 개발·병합 기록을 확인할 수 있습니다.

이 화면에서 확인할 내용

① 의미 있는 Commit 10개 이상

② feature/prompt-list 작업 기록

③ main으로 Merge된 기록

④ Commit 메시지만 보고 변경 내용을 파악할 수 있는지

**## 22. 공개 샘플 Repository Clone**

과제에서는 자신의 저장소가 아니라 공개 샘플 Repository 1개를 clone하여 폴더 구조와 Git log를 확인해야 합니다.

예를 들어 GitHub의 공개 샘플 저장소인 octocat/Hello-World 같은 저장소를 사용할 수 있습니다.

실제 사용할 Repository:

【과제 수행 시 결정】

수행 후:

cd 【clone한 폴더】

dir

git log --oneline

등으로 폴더 구조와 Git 기록을 확인합니다.

📷 증빙

11-clone-verification.png

【이미지 삽입】

그림 11. 공개 샘플 Repository Clone 및 확인

공개 Repository를 git clone으로 내려받은 뒤 폴더 구조와 Git log를 확인한 화면입니다.

힌트: 사용자님 자신의 GitHub Repository를 clone한 화면으로 대체하지 않습니다.

**## 23. .gitignore**

.gitignore는 GitHub에 올릴 필요가 없는 임시파일이나 개발환경 파일을 Git 추적 대상에서 제외하기 위한 파일입니다.

예:

*\*\****\*\*\_\_pycache\_\_\*\***\*\*/

\*.pyc

.venv/

.vscode/

.DS\_Store

Thumbs.db

힌트: Windows에서 확장자가 숨겨져 gitignore.txt가 되지 않도록 실제 파일명이 정확히 .gitignore인지 확인합니다.

과제에서도 .gitignore 생성이 필수입니다.

**## 24. 보너스 기능 — 선택**

과제 원문에는 두 종류의 보너스가 있습니다.

**### Bonus 1 — 저장 및 내보내기**

JSON 파일 저장

JSON 파일 불러오기

전체 프롬프트를 카테고리별 Markdown 파일로 내보내기

**### Bonus 2 — CRUD 및 사용 기록**

프롬프트 수정

프롬프트 삭제

상세 보기 시 조회수 증가

조회수 기준 Top 목록

우리 과제에서 권장하는 추가 사항

Top 목록은 전체를 무한히 출력하기보다 조회수 상위 최대 5개로 제한하는 방식을 고려합니다.

top\_prompts = sorted\_prompts[:5]

**### CRUD란?**

Create → 프롬프트 추가

Read   → 목록 / 검색 / 상세 보기

Update → 프롬프트 수정

Delete → 프롬프트 삭제

힌트: Bonus를 실제 구현한 경우에만 README에 “구현 완료”라고 작성합니다.

**### ⚠️ JSON 구현 시 중요한 주의사항**

필수 과제는 실행 중 추가 데이터가 유지되지만 종료하면 초기화되어야 합니다.

따라서 JSON Bonus를 넣더라도 프로그램이 시작하자마자 자동으로 JSON을 불러와 필수 동작을 영구 저장 방식으로 바꾸는 설계는 피하겠습니다.

안전한 방법은 JSON 저장, JSON 불러오기를 사용자가 명시적으로 선택하는 별도 Bonus 기능으로 만드는 것입니다.

**## 25. 추가 입력 검증 및 실수 방지**

필수 요구사항을 방해하지 않는 범위에서 다음 처리를 적용하는 것을 권장합니다.

빈 제목 → 다시 입력

빈 내용 → 다시 입력

직접 입력 카테고리가 빈 값 → 다시 입력

잘못된 메뉴 번호 → 다시 입력

존재하지 않는 프롬프트 번호 → 안내 후 다시 메뉴

검색 결과 없음 → 안내

카테고리 결과 없음 → 안내

프롬프트 없음 → 안내

힌트: “오류가 발생하지 않았다”보다 어떤 사용자의 실수를 예상하고 어떻게 막았는지 설명합니다.

**## 26. 테스트 결과 및 증빙**

최종 증빙은 기능을 실행했다는 화면이 아니라 기능이 실제로 정상 동작했다는 결과까지 보여주는 것을 원칙으로 합니다.

예:

프롬프트 추가

입력

 ↓

"추가되었습니다"

 ↓

목록 다시 확인

 ↓

3개 → 4개

 ↓

정상 동작 확인

이 방식으로 검색, 즐겨찾기, 카테고리 조회 등도 기능 수행 → 결과 검증까지 보여줍니다.

과제는 개발환경, 프로그램 실행 결과, Git graph 스크린샷을 제출하도록 요구합니다.

**## 27. 문제 해결 및 시행착오**

문제 1. 【실제 발생한 문제】

문제

【무슨 일이 발생했는지】

원인

【왜 발생했는지】

해결

【어떤 명령이나 코드를 수정했는지】

결과

【수정 후 무엇이 정상 동작했는지】

배운 점

【이 문제를 통해 새롭게 알게 된 내용】

힌트: 일부러 문제를 만들 필요는 없습니다. 실제 개발 중 발생한 오류만 기록합니다. 이혜경·강하연 제출물에서 좋았던 문제 → 원인 → 해결 → 결과 → 다음 작업 방식으로 작성합니다.

**## 28. 현재 프로그램의 장점과 한계**

**### 장점**

외부 라이브러리 없이 Python 기본 문법으로 구현

기능별 함수 분리

빈 입력과 잘못된 번호에 대한 입력 검증

제목·내용 키워드 검색

영문 대소문자를 무시하는 검색

실행 중 추가 데이터와 즐겨찾기 상태 유지

Git을 이용한 기능별 변경 이력 관리

**### 한계**

프로그램 종료 시 추가 데이터가 초기화됨

→ 필수 과제의 의도된 동작이므로 오류가 아님

기본 검색에서는 오타 자동 수정 미지원

띄어쓰기 자동 보정 미지원

특수문자 정규화 미지원

정규식 검색 미지원

대규모 데이터 관리에는 적합하지 않음

힌트: “부족해서 못 했다”는 식보다 현재 구현 범위와 향후 발전 가능성을 정확하게 구분합니다.

**## 29. 과제 요구사항 최종 점검표**

이 표는 최종 제출 직전에 실제 결과를 보고 체크합니다.

요구사항        완료    증빙

Python 3.10 이상        ☐       그림 1

Python Extension        ☐       그림 1

Korean Language Pack(선택)      ☐       그림 1

print("Hello") 실행     ☐       그림 1 또는 별도

Git 버전 확인   ☐       그림 1

Git 사용자 이름/이메일 설정     ☐       그림 1

기본 Branch main        ☐       그림 1

VS Code-GitHub 연동     ☐       【증빙】

GitHub Repository 생성  ☐       그림 2

git init        ☐       Git 기록

git add ☐       Git 기록

git commit      ☐       Git 기록

git push        ☐       Git 기록

git pull        ☐       Git 기록

git checkout    ☐       그림 3

git clone       ☐       그림 11

git merge       ☐       그림 3

.gitignore      ☐       Repository

README.md       ☐       Repository

공개 샘플 Repository clone      ☐       그림 11

기본 프롬프트 3개 이상  ☐       그림 5

List + Dictionary       ☐       코드

제목·내용·카테고리·즐겨찾기     ☐       코드

빈 입력 재요청  ☐       실행 결과

직접 카테고리 입력      ☐       실행 결과

추가 시 favorite=False  ☐       코드

실행 중 추가 데이터 유지        ☐       실행 결과

종료 시 초기화  ☐       실행 결과

목록 기능 별도 Branch 개발      ☐       그림 3·4

목록 번호 표시  ☐       그림 5

제목·카테고리·⭐ 표시    ☐       그림 5

빈 목록 안내    ☐       테스트

카테고리별 조회 ☐       그림 7

카테고리 결과 없음 안내 ☐       테스트

제목/내용 검색  ☐       그림 8

검색 결과 없음 안내     ☐       테스트

상세 보기       ☐       그림 9

잘못된 상세 번호 안내   ☐       테스트

즐겨찾기 추가/해제      ☐       그림 10

즐겨찾기 목록   ☐       그림 10

잘못된 메뉴 번호 처리   ☐       테스트

기능 수행 후 메뉴 복귀  ☐       실행 결과

종료 기능       ☐       실행 결과

기능별 함수 분리        ☐       코드

외부 Library 없이 필수기능 구현 ☐       코드

의미 있는 Commit 10개 이상      ☐       그림 4

git log --oneline --graph       ☐       그림 4

GitHub URL 제출 ☐       아래 URL

이 표가 중요한 이유는 과제 원문에서 요구사항이 프로그램 기능뿐 아니라 개발환경·Git 명령·Branch·제출 증빙까지 여러 페이지에 흩어져 있기 때문입니다. 특히 “모든 요구사항을 만족해야 한다”는 전제가 명시되어 있습니다.

**## 30. GitHub Repository**

**### GitHub URL**

【과제 수행 후 실제 URL 입력】

힌트: 최종 제출 전에 Repository가 정상적으로 열리는지 직접 확인하고 URL을 넣습니다.

**## 31. 마무리**

이번 과제를 통해 Python의 변수, List, Dictionary, 조건문, 반복문, 함수 등을 단순히 문법으로 학습하는 데 그치지 않고 실제 프롬프트 관리 프로그램의 기능과 연결하여 활용했습니다.

또한 Git을 사용해 기능별 변경사항을 Commit하고, 별도의 Branch에서 기능을 개발한 뒤 main에 병합하면서 버전 관리의 기본 흐름을 경험했습니다.

가장 어려웠던 부분:

【직접 입력】

해결 과정:

【직접 입력】

이번 과제를 통해 가장 크게 배운 점:

【직접 입력】

앞으로 개선하고 싶은 부분:

【직접 입력】

힌트: 마지막 부분은 AI가 경험을 만들어내면 안 됩니다. 실제 과제를 수행하면서 어려웠던 점과 배운 점을 사용자님이 알려주시면, 그 내용을 자연스러운 보고서 문장으로 제가 다듬겠습니다.

이 README를 만들 때 지킬 핵심 원칙

이번 과제에서는 README를 무조건 길게 만드는 것이 목표가 아닙니다. 과제 원문이 README 자체에 필수로 요구하는 것은 프로그램 이름·간단한 설명·실행 방법·기능 목록·등록된 카테고리 설명입니다. 여기에 사용자님의 목표에 맞게 Python/Git을 모르는 사람도 이해할 최소한의 개념 설명, 선택 이유, 입력 검증, 한계, Git 작업과 증빙 해설을 추가하는 것입니다.

그래서 최종 형태는 “간결한 구성 + 충분한 설명”으로 하되, 화면만 던져놓지 않고 각 그림 바로 아래에 무엇을 했는지와 무엇을 증명하는지를 설명하겠습니다. 또한 필수 기능과 Bonus는 명확히 분리하고, 좋은 추가 기능이라도 필수 요구사항과 충돌하면 넣지 않겠습니다.

특히 지금 단계에서 사용자님이 직접 결정해야 하는 것은 ① 프로젝트/프로그램 이름, ② 이전 미션에서 가져올 실제 기본 프롬프트 3개 이상, ③ Bonus 1·2 구현 여부, ④ 실제 개발 중 발생한 문제와 해결 경험, ⑤ 최종 GitHub URL 정도입니다. 나머지는 실제 개발하면서 제가 이 틀에 맞춰 상당 부분 채워드릴 수 있습니다.

vs code에서 폴더를 만드려고 하는데 이름은 어떻게 할까?

추천은 python-git-prompt-manager 입니다.

이유는 폴더 이름만 봐도 Python + Git 과제 + 프롬프트 관리 프로그램이라는 목적이 바로 드러나고, GitHub 저장소 이름으로 그대로 써도 자연스럽기 때문입니다.

다른 후보도 괜찮습니다.

python-git-prompt-manager ← 가장 추천

prompt-manager-python-git

python-git-first-project

prompt-manager-cli

A1-1-python-git-prompt-manager

이번 과제 제출용이라면 저는 *\*\****\*\*python-git-prompt-manager\*\***\*\*로 만들겠습니다.

VS Code에서 새 폴더를 만들 때도 그대로:

python-git-prompt-manager

로 입력하면 됩니다.

공백이나 한글은 가능하면 피하고, 소문자 + 하이픈(-) 방식으로 가는 게 가장 깔끔합니다.