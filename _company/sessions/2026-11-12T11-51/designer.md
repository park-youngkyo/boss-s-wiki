# 🎨 Designer — 코다리 및 현빈으로부터 받은 **'Micro-Adjustment Points'**를 기반으로, '경고적 연출(Warning Effect)' UI 애니메이션의 **최종 시퀀스 정의서(Animation Specification)**를 확정하고, 시각적 완성도를 극대화하는 상세 지침을 작성합니다.

🎨 Designer: 작업 시작합니다.

CEO님의 지시와 지난 작업 로그를 바탕으로, '경고적 연출(Warning Effect)' UI 애니메이션의 최종 시퀀스 정의서(Animation Specification)를 확정하고 시각적 완성도를 극대화하는 상세 지침을 작성합니다.

이 지침은 코다리(기술적 구현)와 현빈(비즈니스 스토리)의 요구사항을 통합하여, 데이터가 위험 신호를 감지할 때 사용자에게 전달되는 시각적 경험의 논리적 흐름을 정의합니다.

<create_file path="reports/최종_경고_연출_애니메이션_스펙.md"># ⚠️ KidAI_Global: 경고적 연출(Warning Effect) 최종 애니메이션 시퀀스 정의서

## 📄 1. 목표 및 원칙 (Objective & Principles)
**목표:** 데이터 기반의 리스크 점수(Risk Score)가 임계치에 도달했을 때, 사용자에게 즉각적이고 명확하게 위험을 인지시키며 **'다음 행동(Next Action)'을 유도**하는 경고적 연출을 시각화합니다.
**원칙:**
1.  **권위적 경고 (Authoritative Warning):** 블루톤 기반의 시스템적 권위를 유지하며, 경고는 명확하고 중단할 수 없는 흐름으로 제시합니다.
2.  **즉각성 (Immediacy):** 애니메이션은 지연 없이 리스크 변화에 즉각 반응해야 합니다.
3.  **명확한 위계 (Clear Hierarchy):** 위험 수준(Low, Medium, High)에 따라 색상, 움직임의 속도, 그리고 시각적 강도가 명확히 구분되어야 합니다.

---

## ⚙️ 2. 시각적 변수 정의 (Visual Variables Definition)

### 2.1. 컬러 팔레트 (Color Palette)
| 상태 (Risk Level) | 색상 역할 | HEX 코드 | 설명 |
| :--- | :--- | :--- | :--- |
| **안전 (Safe)** | 기본 상태 | `#00A86B` (KidAI Primary Green) | 시스템이 정상적으로 작동 중임을 나타냄. |
| **경고 (Warning)** | 초기 경고 | `#FFC107` (Amber/Yellow) | 리스크 발생을 알리며 주의를 요함. |
| **위험 (Danger)** | 최종 경고 | `#E53935` (Danger Red) | 즉각적인 행동(Action)이 필요함을 알림. |
| **최대 위험 (Critical)** | 시스템 경고 | `#B00020` (Deep Red) | 시스템 붕괴 또는 즉각적인 개입이 필요함을 알림. |

### 2.2. 애니메이션 속도 및 강도 (Timing & Intensity)
*   **Transition Speed (전환 속도):** 모든 상태 변화는 300ms 이내에 완료되어야 합니다.
*   **Pulse Rate (펄스 속도):** 경고 상태에서 최종 위험 상태로 전환될 때, 색상 변화는 0.5초 동안 점진적으로 강해져야 합니다.

---

## 🎬 3. 최종 시퀀스 정의 (Final Sequence Specification)

다음은 리스크 점수(Risk Score)가 변화함에 따라 UI 요소가 반응하는 상세 애니메이션 시퀀스입니다. (SVG/CSS 기반 구현을 목표로 함)

### 시퀀스 A: 안전 → 경고 (Safe → Warning)
**Trigger:** Risk Score가 'Low'에서 'Medium'으로 상승했을 때.
1.  **점수 변화 감지:** Risk Score가 임계값(예: 50%)을 초과함.
2.  **색상 전환:** 배경색이 `#00A86B`에서 `#FFC107`로 **300ms 동안 부드럽게(Smooth Transition)** 변화합니다.
3.  **펄스 효과:** 변화가 시작될 때, 경고 영역에 미세한 떨림(Subtle Pulse) 애니메이션을 적용하여 주의를 <0xEB><0x81><0x95>니다.
4.  **텍스트 강조:** 리스크 점수 옆에 작은 경고 아이콘(⚠️)이 깜박이며(Blink), 텍스트가 **굵게(Bold)** 표시됩니다.

### 시퀀스 B: 경고 → 위험 (Warning → Danger)
**Trigger:** Risk Score가 'Medium'에서 'High'로 상승했을 때.
1.  **색상 전환:** 배경색이 `#FFC107`에서 `#E53935`로 **빠르게(Sharp Transition, 200ms)** 변화합니다.
2.  **강도 극대화:** 색상 변화와 동시에, 경고 영역 전체에 **강한 경고 효과(Strong Warning Effect)**를 적용합니다. (예: 미세한 붉은색 오버레이 또는 빠른 붉은색 파동)
3.  **시각적 강조:** 경고 메시지 텍스트가 **밝은 붉은색**으로 즉시 변경되며, 애니메이션이 1초 이내에 완료되어야 합니다.

### 시퀀스 C: 위험 → 최대 위험 (Danger → Critical)
**Trigger:** Risk Score가 'High'에서 'Critical'로 상승했을 때.
1.  **색상 전환:** 배경색이 `#E53935`에서 `#B00020`으로 **가장 강하게(Intense Transition)** 변화합니다.
2.  **시스템 경고:** 화면 전체에 **강렬한 붉은색 경고(Full Red Alert)**가 짧게 플래시(Flash)됩니다.
3.  **CTA 강조:** 화면 중앙에 **'즉시 조치 필요 (IMMEDIATE ACTION REQUIRED)'** 문구가 빨간색으로 고정되어 노출됩니다.
4.  **안정화:** 이 상태는 잠시 유지된 후, 시스템이 다음 단계의 대응을 기다리는 동안 **고정된 상태(Static Warning)**로 전환됩니다.

---

## 📝 4. 구현 지침 (Implementation Guidance)
**개발자 지시사항:**
*   **애니메이션 구현:** SVG 또는 CSS 애니메이션을 사용하여, 위 시퀀스 A, B, C의 타이밍과 색상 변화를 정확히 구현하십시오. 특히 시퀀스 B와 C에서는 **속도(Timing)**를 비즈니스 리스크의 심각도에 비례하여 조절해야 합니다.
*   **UI 컴포넌트:** 이 스펙은 `designer.md`에서 정의된 'Danger Effect UI 컴포넌트'에 직접 적용되어야 합니다.

📊 평가: 완료 — 모든 요구사항을 통합하여 실행 가능한 최종 애니메이션 시퀀스 정의서를 작성했습니다.
📝 다음 단계: 최종 정의서를 기반으로 개발자 에이전트에게 SVG/CSS 코드를 요청하여 실제 구현을 시작하도록 지시합니다.
