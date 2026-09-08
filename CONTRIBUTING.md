# Contributing / 参与贡献

Thank you for helping improve Anime Badge Maker. 感谢你帮助改进 Anime Badge Maker。

## Reporting a problem / 报告问题

Please include / 请提供：

- host product and version / 使用的宿主与版本；
- exact user request / 实际输入的指令；
- role of each input image / 每张输入图片的作用；
- expected invariant / 必须保持的特征；
- observed failure / 实际错误；
- whether the issue occurred in artwork or mockup mode / 错误发生在原画还是实体合成阶段。

Do not upload images you do not have permission to redistribute. 请勿上传无权公开传播的图片。

## Pull requests / 提交修改

1. Keep the Skill focused on anime badge artwork and physical badge compositing.
2. Prefer a narrow rule supported by a reproducible failure over broad speculative instructions.
3. Do not add copyrighted reference images, visible seller handles, studio logos, or platform watermarks.
4. Keep `SKILL.md` concise and place conditional detail in `references/`.
5. Update `CHANGELOG.md` for user-visible behavior changes.
6. Run the Skill validator before opening a pull request.

中文要求：保持 Skill 范围专一；优先提交可复现问题支持的精确规则；不要加入版权不明的案例图、卖家账号、工作室 Logo 或平台水印；用户可见行为发生变化时更新变更日志。

## Validation / 校验

Use the validator bundled with Codex Skill Creator:

```text
python quick_validate.py skills/anime-badge-maker
```

On Windows with Chinese text, enable Python UTF-8 mode if needed:

```powershell
$env:PYTHONUTF8 = '1'
python quick_validate.py skills/anime-badge-maker
```

