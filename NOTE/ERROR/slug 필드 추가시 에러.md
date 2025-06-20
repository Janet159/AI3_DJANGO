It is impossible to add a non-nullable field 'slug' to post without specifying a default. This is because the database needs lt. This is because the database needs something to populate existing rows.
Please select a fix:
 1) Provide a one-off default now (will be set on all existing rows with a null value for this column)
for this column)
 2) Quit and manually define a default value in models.py.

---
이건 기존 데이터가 있기 때문에, 기본값을 지정하지 않고는 slug라는 null 허용 안하는 필드를 post 테이블에 추가할 수 없다는 뜻이다.
데이터베이스는 기존에 이미 있는 데이터 행들에 이 새 필드를 채울 값을 필요로 한다.
해결 방법을 선택하라:

1) 지금 임시 기본값을 제공해라 (이 값이 현재 존재하는 모든 row에 적용될 것이다).

2) 종료하고 models.py에서 기본값을 수동으로 정의해라.

---
## 해결
```
    slug = models.SlugField(max_length=200, unique=True, null = True)
```
우선적으로, null 허용 지정하고 마이그레이션 후, null=False를 변경하는 방법으로 해결!