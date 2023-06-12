# Raw Query

## コンピュータを表示

MATCH (m:Computer) RETURN m


## ユーザーを表示

MATCH (m:User) RETURN m

## アクティブなセッションを表示

MATCH p = (c:Computer)-[:HasSession]->(m:User) RETURN p
