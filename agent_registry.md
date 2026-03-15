# 📋 Agent Registry — Danh mục Agent

> **File này là cache tham khảo nhanh.** Source of truth luôn là filesystem (`agents/`).
> Manager phải chạy Auto-Discovery trước mỗi phiên làm việc mới để phát hiện agent mới.

## Cách thêm agent mới

Chỉ cần đặt thư mục agent mới vào `agents/` với cấu trúc tối thiểu:
```
agents/
  my-new-agent/
    AGENT.md (hoặc instructions.md hoặc README.md)
    skills/
      skill-name/
        SKILL.md
```
Manager sẽ **tự động phát hiện** agent mới ở lần quét tiếp theo.

---

## Agent hiện có (snapshot)

### 1. template_content_agent
- **Mô tả:** Tạo nội dung template, tài liệu docx/pdf, outline nghiên cứu AI
- **File nhận diện:** `AGENT.md`
- **Đường dẫn:** `../template_content_agent/`
- **Skills:**
  | Skill | Path |
  |-------|------|
  | ai_research_outlines | `../template_content_agent/skills/ai_research_outlines/SKILL.md` |
  | ai_research_guidance | `../template_content_agent/skills/ai_research_guidance/SKILL.md` |
  | official_claude_docx | `../template_content_agent/skills/official_claude_docx/SKILL.md` |
  | official_claude_doc_coauthoring | `../template_content_agent/skills/official_claude_doc_coauthoring/SKILL.md` |
  | official_claude_pdf | `../template_content_agent/skills/official_claude_pdf/SKILL.md` |

### 2. Research_Trend_Agent
- **Mô tả:** Nghiên cứu xu hướng, phân tích trend, brainstorming ý tưởng nghiên cứu
- **File nhận diện:** `AGENT.md` ✅ (standardized)
- **Đường dẫn:** `../Research_Trend_Agent/`
- **Skills:**
  | Skill | Path |
  |-------|------|
  | deep-research | `../Research_Trend_Agent/skills/deep-research/SKILL.md` |
  | apify-trend-analysis | `../Research_Trend_Agent/skills/apify-trend-analysis/SKILL.md` |
  | brainstorming-research-ideas | `../Research_Trend_Agent/skills/brainstorming-research-ideas/SKILL.md` |
  | creative-thinking-for-research | `../Research_Trend_Agent/skills/creative-thinking-for-research/SKILL.md` |
  | context7-auto-research | `../Research_Trend_Agent/skills/context7-auto-research/SKILL.md` |
  | research-engineer | `../Research_Trend_Agent/skills/research-engineer/SKILL.md` |

### 3. TikZ-Drawing-Agent
- **Mô tả:** Vẽ hình TikZ/LaTeX — sơ đồ mạch, flowchart, graph, block diagram
- **File nhận diện:** `AGENT.md` ✅ (standardized)
- **Đường dẫn:** `../TikZ-Drawing-Agent/`
- **Skills:**
  | Skill | Path |
  |-------|------|
  | tikz-code-generator | `../TikZ-Drawing-Agent/skills/tikz-code-generator/SKILL.md` |
  | tikz-library-selector | `../TikZ-Drawing-Agent/skills/tikz-library-selector/SKILL.md` |
  | image-analyzer | `../TikZ-Drawing-Agent/skills/image-analyzer/SKILL.md` |
  | latex-compiler | `../TikZ-Drawing-Agent/skills/latex-compiler/SKILL.md` |
  | iterative-refiner | `../TikZ-Drawing-Agent/skills/iterative-refiner/SKILL.md` |

### 4. Science_Scholar_Agent
- **Mô tả:** Chuyên gia KHKT — Giám khảo VISEF, Phản biện khoa học, Tái tạo mô hình, viết paper ML/AI
- **File nhận diện:** `AGENT.md` ✅ (updated)
- **Đường dẫn:** `../Science_Scholar_Agent/`
- **Skills:**
  | Category | Skill | Path |
  |----------|-------|------|
  | Evaluation | lm-evaluation-harness | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/11-evaluation/lm-evaluation-harness/SKILL.md` |
  | Evaluation | bigcode-evaluation-harness | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/11-evaluation/bigcode-evaluation-harness/SKILL.md` |
  | Evaluation | nemo-evaluator | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/11-evaluation/nemo-evaluator/SKILL.md` |
  | Agents | langchain | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/langchain/SKILL.md` |
  | Agents | llamaindex | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/llamaindex/SKILL.md` |
  | Agents | crewai | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/crewai/SKILL.md` |
  | Agents | autogpt | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/autogpt/SKILL.md` |
  | Prompt Eng. | dspy | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/dspy/SKILL.md` |
  | Prompt Eng. | guidance | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/guidance/SKILL.md` |
  | Prompt Eng. | instructor | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/instructor/SKILL.md` |
  | Prompt Eng. | outlines | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/outlines/SKILL.md` |
  | Paper Writing | ml-paper-writing | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/20-ml-paper-writing/SKILL.md` |
  | Ideation | brainstorming-research-ideas | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/21-research-ideation/brainstorming-research-ideas/SKILL.md` |
  | Ideation | creative-thinking-for-research | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/21-research-ideation/creative-thinking-for-research/SKILL.md` |
  | Antigravity | code-review-ai | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/code-review-ai-ai-review/SKILL.md` |
  | Antigravity | data-scientist | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/data-scientist/SKILL.md` |
  | Antigravity | evaluation | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/evaluation/SKILL.md` |
  | Antigravity | research-engineer | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/research-engineer/SKILL.md` |

### 5. Academic-Writing-Agent
- **Mô tả:** Viết và phân tích văn bản học thuật, trích xuất highlight, map & rewrite
- **File nhận diện:** `AGENT.md` ✅ (standardized)
- **Đường dẫn:** `../Academic-Writing-Agent/`
- **Skills:**
  | Skill | Path |
  |------|------|
  | turnitin-segment-extractor | `../Academic-Writing-Agent/skills/turnitin-segment-extractor/SKILL.md` |
  | turnitin-dedup-cleaner | `../Academic-Writing-Agent/skills/turnitin-dedup-cleaner/SKILL.md` |
  | manuscript-paragraph-mapper | `../Academic-Writing-Agent/skills/manuscript-paragraph-mapper/SKILL.md` |
  | manuscript-humanizer | `../Academic-Writing-Agent/skills/manuscript-humanizer/SKILL.md` |
  | ai-writing-pattern-analyzer | `../Academic-Writing-Agent/skills/ai-writing-pattern-analyzer/SKILL.md` |

  **Tool-backed scripts:**
  | Tool | Path |
  |------|------|
  | step1_extract | `../Academic-Writing-Agent/tools/step1_extract.py` |
  | step2_dedup | `../Academic-Writing-Agent/tools/step2_dedup.py` |
  | step3_map_and_rewrite | `../Academic-Writing-Agent/tools/step3_map_and_rewrite.py` |
  | step4_inject | `../Academic-Writing-Agent/tools/step4_inject.py` |
  | analyze_text | `../Academic-Writing-Agent/analyze_text.py` |
  | extract_highlights | `../Academic-Writing-Agent/extract_highlights.py` |

### 6. EE_Edu_Innovator_Agent
- **Mô tả:** Giáo dục Kỹ thuật Điện — thiết kế chương trình, phương pháp sư phạm, đánh giá
- **File nhận diện:** `AGENT.md` ✅ (standardized)
- **Đường dẫn:** `../EE_Edu_Innovator_Agent/`
- **Skills:**
  | Skill | Path |
  |-------|------|
  | curriculum-architect | `../EE_Edu_Innovator_Agent/skills/curriculum-architect/SKILL.md` |
  | pedagogy-strategist | `../EE_Edu_Innovator_Agent/skills/pedagogy-strategist/SKILL.md` |
  | ee-concept-demystifier | `../EE_Edu_Innovator_Agent/skills/ee-concept-demystifier/SKILL.md` |
  | lab-project-designer | `../EE_Edu_Innovator_Agent/skills/lab-project-designer/SKILL.md` |
  | assessment-evaluator | `../EE_Edu_Innovator_Agent/skills/assessment-evaluator/SKILL.md` |
  | trend-research-advisor | `../EE_Edu_Innovator_Agent/skills/trend-research-advisor/SKILL.md` |

### 7. Web_Intelligence_Agent
- **Mô tả:** Tra cứu thông tin trực tuyến, crawl website, tương tác trình duyệt, truy vết link tải, tải file và đọc nội dung đã tải
- **File nhận diện:** `AGENT.md` ✅ (new)
- **Đường dẫn:** `../Web_Intelligence_Agent/`
- **Skills:**
  | Skill | Path |
  |-------|------|
  | current-web-search | `../Web_Intelligence_Agent/skills/current-web-search/SKILL.md` |
  | source-verification | `../Web_Intelligence_Agent/skills/source-verification/SKILL.md` |
  | site-crawler | `../Web_Intelligence_Agent/skills/site-crawler/SKILL.md` |
  | browser-interaction | `../Web_Intelligence_Agent/skills/browser-interaction/SKILL.md` |
  | direct-link-downloader | `../Web_Intelligence_Agent/skills/direct-link-downloader/SKILL.md` |
  | downloaded-pdf-reader | `../Web_Intelligence_Agent/skills/downloaded-pdf-reader/SKILL.md` |
  | downloaded-docx-reader | `../Web_Intelligence_Agent/skills/downloaded-docx-reader/SKILL.md` |
  | semantic-web-search | `../Web_Intelligence_Agent/skills/semantic-web-search/SKILL.md` |
  | deep-online-research | `../Web_Intelligence_Agent/skills/deep-online-research/SKILL.md` |
  | platform-scraper | `../Web_Intelligence_Agent/skills/platform-scraper/SKILL.md` |
  | technical-doc-fetcher | `../Web_Intelligence_Agent/skills/technical-doc-fetcher/SKILL.md` |

---

## Auto-Discovery Protocol

Khi quét lần tới, Manager chạy logic sau:

```
for each directory in agents/:
  if directory == "agent-manager": skip
  look for: AGENT.md → instructions.md → requirement.md → README.md → agent_config.yaml
  look for: skills/**/SKILL.md
  register agent with: {name, description_file, skill_paths[]}
```

Bất kỳ agent nào có ít nhất 1 file nhận diện sẽ được đăng ký tự động.
