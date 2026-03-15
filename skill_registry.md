# 🗺️ Skill Registry — Bản đồ Skill toàn hệ thống

> **Quy tắc gọi skill:** Luôn dùng đường dẫn tương đối từ thư mục `agent-manager/`.
> Cách này hoạt động đồng nhất trên cả **Copilot** và **Codex** vì cả hai đều đọc file qua filesystem.

## Universal Skill Path Convention

```
../[agent-folder-name]/skills/[skill-path]/SKILL.md
```

**Ví dụ:**
```
../Research_Trend_Agent/skills/deep-research/SKILL.md
../template_content_agent/skills/official_claude_docx/SKILL.md
../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/langchain/SKILL.md
```

**Cách sử dụng trên Copilot:**
```
Đọc file agents/agent-manager/AGENT.md, sau đó thực thi task...
```

**Cách sử dụng trên Codex:**
```
Đọc file agents/agent-manager/AGENT.md, sau đó thực thi task...
```

> Cả hai platform đều follow cùng cơ chế: đọc AGENT.md → đọc skill_registry → đọc SKILL.md → thực thi.

---

## Phân loại Skill theo năng lực

### 📝 Content & Document Creation
| Skill | Agent | Path |
|-------|-------|------|
| ai_research_outlines | template_content_agent | `../template_content_agent/skills/ai_research_outlines/SKILL.md` |
| ai_research_guidance | template_content_agent | `../template_content_agent/skills/ai_research_guidance/SKILL.md` |
| official_claude_docx | template_content_agent | `../template_content_agent/skills/official_claude_docx/SKILL.md` |
| official_claude_doc_coauthoring | template_content_agent | `../template_content_agent/skills/official_claude_doc_coauthoring/SKILL.md` |
| official_claude_pdf | template_content_agent | `../template_content_agent/skills/official_claude_pdf/SKILL.md` |
| ml-paper-writing | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/20-ml-paper-writing/SKILL.md` |

### 🔬 Research & Trend Analysis
| Skill | Agent | Path |
|-------|-------|------|
| deep-research | Research_Trend_Agent | `../Research_Trend_Agent/skills/deep-research/SKILL.md` |
| apify-trend-analysis | Research_Trend_Agent | `../Research_Trend_Agent/skills/apify-trend-analysis/SKILL.md` |
| context7-auto-research | Research_Trend_Agent | `../Research_Trend_Agent/skills/context7-auto-research/SKILL.md` |
| research-engineer | Research_Trend_Agent | `../Research_Trend_Agent/skills/research-engineer/SKILL.md` |
| trend-research-advisor | EE_Edu_Innovator_Agent | `../EE_Edu_Innovator_Agent/skills/trend-research-advisor/SKILL.md` |

### 💡 Ideation & Creative Thinking
| Skill | Agent | Path |
|-------|-------|------|
| brainstorming-research-ideas | Research_Trend_Agent | `../Research_Trend_Agent/skills/brainstorming-research-ideas/SKILL.md` |
| creative-thinking-for-research | Research_Trend_Agent | `../Research_Trend_Agent/skills/creative-thinking-for-research/SKILL.md` |
| brainstorming-research-ideas (Scholar) | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/21-research-ideation/brainstorming-research-ideas/SKILL.md` |
| creative-thinking (Scholar) | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/21-research-ideation/creative-thinking-for-research/SKILL.md` |

### 🎨 Visualization & Drawing
| Skill | Agent | Path |
|-------|-------|------|
| tikz-code-generator | TikZ-Drawing-Agent | `../TikZ-Drawing-Agent/skills/tikz-code-generator/SKILL.md` |
| tikz-library-selector | TikZ-Drawing-Agent | `../TikZ-Drawing-Agent/skills/tikz-library-selector/SKILL.md` |
| image-analyzer | TikZ-Drawing-Agent | `../TikZ-Drawing-Agent/skills/image-analyzer/SKILL.md` |
| latex-compiler | TikZ-Drawing-Agent | `../TikZ-Drawing-Agent/skills/latex-compiler/SKILL.md` |
| iterative-refiner | TikZ-Drawing-Agent | `../TikZ-Drawing-Agent/skills/iterative-refiner/SKILL.md` |

### 🤖 AI/ML Frameworks & Evaluation
| Skill | Agent | Path |
|-------|-------|------|
| lm-evaluation-harness | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/11-evaluation/lm-evaluation-harness/SKILL.md` |
| bigcode-evaluation-harness | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/11-evaluation/bigcode-evaluation-harness/SKILL.md` |
| nemo-evaluator | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/11-evaluation/nemo-evaluator/SKILL.md` |
| langchain | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/langchain/SKILL.md` |
| llamaindex | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/llamaindex/SKILL.md` |
| crewai | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/crewai/SKILL.md` |
| autogpt | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/14-agents/autogpt/SKILL.md` |

### 🧠 Prompt Engineering
| Skill | Agent | Path |
|-------|-------|------|
| dspy | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/dspy/SKILL.md` |
| guidance | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/guidance/SKILL.md` |
| instructor | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/instructor/SKILL.md` |
| outlines | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/AI-Research-SKILLs/16-prompt-engineering/outlines/SKILL.md` |

### 🔍 Code Review & Data Science
| Skill | Agent | Path |
|-------|-------|------|
| code-review-ai | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/code-review-ai-ai-review/SKILL.md` |
| data-scientist | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/data-scientist/SKILL.md` |
| evaluation (antigravity) | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/evaluation/SKILL.md` |
| research-engineer (antigravity) | Science_Scholar_Agent | `../Science_Scholar_Agent/skills/antigravity-awesome-skills/research-engineer/SKILL.md` |

### ✍️ Academic Writing
| Tool | Agent | Path |
|------|-------|------|
| step1_extract | Academic-Writing-Agent | `../Academic-Writing-Agent/tools/step1_extract.py` |
| step2_dedup | Academic-Writing-Agent | `../Academic-Writing-Agent/tools/step2_dedup.py` |
| step3_map_and_rewrite | Academic-Writing-Agent | `../Academic-Writing-Agent/tools/step3_map_and_rewrite.py` |
| step4_inject | Academic-Writing-Agent | `../Academic-Writing-Agent/tools/step4_inject.py` |
| analyze_text | Academic-Writing-Agent | `../Academic-Writing-Agent/analyze_text.py` |
| extract_highlights | Academic-Writing-Agent | `../Academic-Writing-Agent/extract_highlights.py` |

### 🎓 EE Education
| Skill | Agent | Path |
|-------|-------|------|
| curriculum-architect | EE_Edu_Innovator_Agent | `../EE_Edu_Innovator_Agent/skills/curriculum-architect/SKILL.md` |
| pedagogy-strategist | EE_Edu_Innovator_Agent | `../EE_Edu_Innovator_Agent/skills/pedagogy-strategist/SKILL.md` |
| ee-concept-demystifier | EE_Edu_Innovator_Agent | `../EE_Edu_Innovator_Agent/skills/ee-concept-demystifier/SKILL.md` |
| lab-project-designer | EE_Edu_Innovator_Agent | `../EE_Edu_Innovator_Agent/skills/lab-project-designer/SKILL.md` |
| assessment-evaluator | EE_Edu_Innovator_Agent | `../EE_Edu_Innovator_Agent/skills/assessment-evaluator/SKILL.md` |

---

## 🔄 Dynamic Discovery

Bảng trên chỉ là snapshot. Để phát hiện skill mới:

```bash
# Lệnh quét tất cả SKILL.md trong agents/
find ../  -path "*/skills/**/SKILL.md" -not -path "*/agent-manager/*" | sort
```

Manager tự chạy scan tương đương mỗi khi khởi tạo phiên làm việc mới.

## 📌 Quy tắc chọn skill

1. **Exact match first** — Nếu task khớp chính xác 1 skill → dùng skill đó
2. **Category match** — Nếu không khớp chính xác → chọn agent có category phù hợp nhất
3. **Multi-skill combo** — Nếu task phức tạp → kết hợp skill từ nhiều agent
4. **Overlap resolution** — Khi 2 agent có skill tương tự (e.g. brainstorming), ưu tiên agent chuyên sâu hơn về domain của task
