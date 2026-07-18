# Static SvelteKit Site

This project is configured as a fully prerendered static site. `pnpm build` produces deployable files in `build/`.

## Local development

```sh
pnpm dev
pnpm build
pnpm preview
```

## コンテンツの追加

メンバー、書籍、出展イベントはすべて [src/routes/+page.svelte](src/routes/+page.svelte) の先頭にある `members`、`books`、`events` 配列で管理しています。各配列にオブジェクトを追加すると、紹介ページにも自動的に表示されます。

### メンバー

`id` は配列内で重複しない値にします。`iconUrl` は任意で、画像を使わない場合は空文字にすると `initial` が表示されます。アイコン画像は `static/members/` に配置し、`iconUrl` には `static` を除いた公開パスを指定します。

```ts
{
	id: 'member-4',
	name: 'メンバー名',
	role: '担当・得意分野',
	initial: 'M',
	iconUrl: '/members/member-4.jpg',
	xUrl: 'https://x.com/ユーザー名',
	githubUrl: 'https://github.com/ユーザー名',
}
```

### 書籍

`id` は配列内で重複しない値にします。`color` は `coral`、`yellow`、`blue` の定義済みカラーに加え、`#E9573F` のような CSS カラーコードも指定できます。`coverUrl` は任意で、表紙画像を使う場合は `static/books/` に配置して、`static` を除いた公開パスを指定します。未指定の場合は `color` を使った文字入りの表紙が表示されます。`url` は任意で、値を設定した書籍だけカード全体がリンクになります。リンクにしない場合は空文字にします。

```ts
{
	id: 'book-4',
	title: '書籍タイトル',
	description: '書籍の紹介文を入力します。',
	category: '技術書',
	color: '#E9573F',
	coverUrl: '/books/book-4.jpg',
	url: 'https://example.com/book',
}
```

### 出展イベント

`id` は配列内で重複しない値にします。イベントの日付、名称、会場・スペース番号、出展状況を入力します。`eventUrl` は任意で、値を設定すると矢印が表示され、クリックでイベント詳細ページを開きます。リンクを表示しない場合は空文字にします。

```ts
{
	id: 'event-3',
	date: '2026.08.16',
	name: 'イベント名',
	venue: '会場名・スペース番号',
	status: '出展予定',
	eventUrl: 'https://example.com/event',
}
```

## GitHub Pages Hosting

このリポジトリは GitHub Actions で自動的に GitHub Pages へデプロイされます。`main` ブランチへのプッシュ時に `.github/workflows/deploy.yml` が実行され、`build/` の成果物が公開されます。

初回デプロイ前に、リポジトリの **Settings → Pages** で Source を **GitHub Actions** に設定してください。
