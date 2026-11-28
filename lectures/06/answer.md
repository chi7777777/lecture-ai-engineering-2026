# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：agent[search_materials][make_quiz],mcp_agent[glossary_search_glossary]
- STEP 2 の [tool call]：glossary_search_glossary({'query': '3レベル'})
- STEP 3 の [tool call]：fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- STEP 4 の [tool call]：2回 aws_aws___search_documentation({'search_phrase': 'Amazon S3 バージョニング 概要'}), aws_aws___search_documentation({'search_phrase': 'Using versioning in S3 buckets', 'topics': ['general']})
- 気づき・疑問：uv run python -m app.mcp_agent --trace "https://knowledge-mcp.global.api.aws/ の冒頭を日本語で 3行に要約して "を実行したら、"指定されたURL（`https://knowledge-mcp.global.api.aws/`）へのアクセスが、対象サイトのアクセス制御（robots.txtなど）により自動取得が制限されているため、直接ページの内容を取得することができませんでした。" のエラーになった。

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎
- やったこと：app/mcp_server.py に get_lecture_summary を追加
- 結果：モデルに見えているツールが 7 → 8個([glossary_get_lecture_summary]が追加)され、uv run python -m app.mcp_agent --trace "第2回では何を学びますか？ "の実行で、[tool call]glossary_get_lecture_summary({'lecture': 2})が呼ばれた。
- 気づき・疑問：どのツールを呼ぶかは、mcp_agent.pyのINSTRUCTIONSに従っていると思うが、どのような質問にも対応するINSTRUCTIONSを作るのは大変そうだと思った。
