# AI · 데이터 · OpenCV 학습
[← 포트폴리오](README.md)

## 곤충 4종 분류·객체 탐지 실험

[발표 PDF](evidence-insect-study.pdf) · [4차 지표 PDF](evidence-insect-metrics.pdf)

양봉꿀벌·뒤영벌·말벌·꽃등에의 위치와 종류를 구분하는 Intel Geti 실험 자료를 확인했습니다.

| 단계 | 변경 사항 | 자료가 보여주는 범위 |
|---|---|---|
| 1차 | 이미지 Classification | 사진 전체의 종류 분류 |
| 2차 | Detection 전환 | 배경 영향과 위치 탐지를 함께 검토 |
| 3차 | YOLOX-S와 사진 보강 | 데이터 보강만으로 모든 라벨이 좋아지지는 않음 |
| 4차 | 같은 440장·4라벨에서 DFine-X 선택 | 모델 선택 변경 후 테스트 지표 비교 |

발표자료에서 4차 테스트 F-measure는 네 라벨 모두 1로 표시됩니다. 48장 평가 화면의 Score는 YOLOX-S 86, DFine-X 94입니다. **테스트 분할 지표·화면의 Score·새 사진 정확도는 서로 다릅니다.** 이 수치를 일반 환경 정확도 100%로 해석하지 않습니다. 원시 평가 로그와 동일 분할 여부를 재검증하지 않았습니다.

Drive의 이름 없는 Google 문서는 텍스트 없이 곤충 탐지 결과 이미지 26개를 담고 있었습니다. 결과를 확인했으나, 외부 원본 이미지 권리를 확인하지 않은 상태에서 이미지 묶음을 재배포하지는 않았습니다.

## 데이터셋 제작 도구

[스크립트·설정 5개](source-dataset-tools.zip)

고양이/개 데이터셋 제작 스크립트와 helmet/vest 제작 도구에서 다운로드, 파일 후보 선택, 이미지 변환, 해시·박스 정보 처리 흐름을 확인했습니다. 이 도구를 실행하거나 외부 이미지를 새로 수집하지 않았습니다. 이미지 원본과 모델 가중치는 공개 포트폴리오에 중복 업로드하지 않았습니다.

## Colab 노트북

[출력·개인 메타데이터를 제거한 노트북 8개](source-notebooks.zip)

| 파일 | 확인한 코드·상태 |
|---|---|
| test0312.ipynb | pandas, numpy, matplotlib, TensorFlow/Keras 사용 |
| Untitled0.ipynb | pandas, TensorFlow/Keras, sklearn 사용 |
| Untitled1.ipynb | Python 기초 실습 코드 |
| intro.ipynb | 짧은 입문 코드 |
| Ted MNIST MLP 사본 | MNIST·MLP 학습 자료의 사본 |
| Ted MobileNetV2 Fashion MNIST 사본 | 전이학습 관련 교육자료의 사본 |
| BigData0903 / Untitled | 코드 셀이 비어 있어 프로젝트 성과로 소개하지 않음 |

교육자료 사본은 학습 기록으로 구분하며 직접 설계한 모델 성과로 제시하지 않습니다. 저장된 출력·실행 횟수·사용자 메타데이터를 제거했고 학습을 다시 돌리지 않았습니다.

## OpenCV

[실습 스크립트 18개](source-opencv-practice.zip)

이미지 읽기·쓰기, 색 공간, 자르기·크기 변경, 반전, 이진화, 블러, 에지, 영상 합성, 논리 연산, 채널 분리, 동영상·카메라 미리보기, GUI 트랙바를 다룹니다. 학생용 실습 자료로 분류하며 독자적인 비전 알고리즘 개발 성과로 주장하지 않습니다.

## 추가 기초 학습

[AI_PGM](https://github.com/seo219/AI_PGM)은 Python 문법·함수·클래스·파일 입출력 학습 기록입니다. [OOP](https://github.com/seo219/OOP)에는 Python 외에 C++ 도서관리·계산기 소스도 있습니다. 빈 저장소·단순 Git 연습 저장소는 대표 프로젝트에서 제외했습니다.
