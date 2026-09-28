# Mandatory Cross-Project Git Delivery (2026-09-29)

所有實作、修復、文件、原型、技能與 Wiki 倉庫變更均須遵守 [跨專案 Git 交付規範](https://github.com/chevalier1216/KarpathyWiki_personal/blob/main/CROSS_PROJECT_GIT_POLICY.md)；不得 direct commit/push 預設整合分支（既有 main/master，或正式切換前的當前 default）。專案個別規格、驗證、授權、費用防護不變；如與舊的 direct-to-main 指示衝突，以此政策為準。

1. 先讀最新整合分支，獨立任務建立 `feat/*` / `fix/*` / `docs/*` / `chore/*` 短期 branch；同時開發不同功能則獨立 branch、PR 及必要的隔離工作樹。
2. 在 branch 修改 → 執行適當測試/文件連結檢查與敏感資訊掃描 → commit → push branch → GitHub Pull Request（PR / Merge Request），關聯相關 Issue。
3. PR 須有目的/範圍、測試及 CI 證據、相依項、風險、資料或 migration/部署與回檔方案；CI 未過、衝突未解或重大風險未審查不得 merge。
4. 預設 Squash Merge 到受保護整合分支；部署者在合併後確認正式結果。回報 Base、Branch、PR URL、Head SHA、CI、Merge SHA、Deploy/Readback、Revert 方法；PR pending 就標 pending，不能宣稱完成。
5. 回檔透過新 `revert/*` 分支與 PR，絕不 force push/reset 整合分支；外部資料/DB/附件需另外的可行回復措施。
6. 禁止因 Agent、Codex/Work 額度、工具限制、緊急修正而自行繞過 PR。僅使用者對單次例外明確核准才可考慮；GitHub Ruleset 應另設定 Require PR / Required checks / Block force push/deletion 並讀回，文件本身不等於保護已啟用。

使用者無須每次重述這些工作流規則；由執行 Agent 自動遵守。
