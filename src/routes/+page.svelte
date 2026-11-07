<script lang="ts">
	import { base } from '$app/paths'

	const members = [
		{
			id: 'member-1',
			name: 'みどり',
			role: 'AWS, TypeScript, Ruby',
			initial: 'M',
			iconUrl: '/members/midori.jpg',
			xUrl: 'https://x.com/ryder472',
			githubUrl: 'https://github.com/ryder472',
		},
		{
			id: 'member-2',
			name: 'hayao',
			role: 'Java,LLM',
			initial: 'H',
			iconUrl: '/members/hayao.png',
			xUrl: 'https://x.com/hayao099',
			githubUrl: 'https://github.com/hayao099',
		},
		{
			id: 'member-3',
			name: 'よしお',
			role: 'LLM・GAS',
			initial: 'Y',
			iconUrl: '/members/yoshio.png',
			xUrl: 'https://x.com/yoshi0_dj',
			githubUrl: 'https://github.com/yoshi0dj',
		},
		{
			id: 'member-4',
			name: 'Kushizam',
			role: 'Python, Laravel, React',
			initial: 'K',
			iconUrl: '/members/kushizam.jpg',
			xUrl: 'https://x.com/kushizam',
			githubUrl: 'https://github.com/kushizam',
		},
	]

	const books = [
		{
			id: 'book-1',
			title: '書籍タイトル',
			description: 'ここに書籍の紹介文を入力します。',
			category: '技術書',
			color: 'coral',
			coverUrl: '',
			url: '',
		},
		{
			id: 'book-2',
			title: '書籍タイトル',
			description: 'ここに書籍の紹介文を入力します。',
			category: '技術書',
			color: 'yellow',
			coverUrl: '',
			url: '',
		},
		{
			id: 'book-3',
			title: '書籍タイトル',
			description: 'ここに書籍の紹介文を入力します。',
			category: '技術書',
			color: 'blue',
			coverUrl: '',
			url: '',
		},
	]

	const bookCoverColors: Record<string, string> = {
		coral: '#e9573f',
		yellow: '#f6d95e',
		blue: '#9acfc7',
	}
	const events = [
		{
			id: 'event-1',
			date: '2026.11.21-2026.12.6',
			name: '技術書典21',
			venue: 'オンライン / 11/23のみ 池袋・サンシャインシティ 展示ホールD（文化会館ビル2F）- そ04',
			status: '出展',
			eventUrl: 'https://techbookfest.org/event/tbf21/market',
		},
	]
</script>

<svelte:head>
	<title>技術加速研究所</title>
	<meta
		name="description"
		content="技術加速研究所は、技術同人誌サークルです。"
	/>
</svelte:head>

<header class="site-header">
	<a class="wordmark" href="#top" aria-label="技術加速研究所 トップへ">
		<span>技術加速研究所</span>
	</a>
	<nav aria-label="ページ内ナビゲーション">
		<a href="#books">書籍</a>
		<a href="#members">メンバー</a>
		<a href="#events">出展予定</a>
	</nav>
</header>

<main id="top">
	<section class="hero" aria-labelledby="hero-title">
		<div class="hero-copy">
			<p class="eyebrow">ギジュツ カソク ラボ</p>
			<h1 id="hero-title">技術加速研究所</h1>
			<p class="hero-lead">もっと加速し､その先へ。</p>
			<a class="hero-link" href="#books">書籍を見る <span aria-hidden="true">→</span></a>
		</div>
		<div class="hero-art" aria-hidden="true">
			<p class="hero-art-label">ISSUE / 01-03</p>
			<div class="book-stack">
				<div class="hero-book hero-book-back">
					<span>TECHNICAL<br />ZINE</span>
				</div>
				<div class="hero-book hero-book-middle">
					<span>MAKE<br />MORE</span>
				</div>
				<div class="hero-book hero-book-front">
					<p>技術加速研究所</p>
					<strong>つくる<br />学ぶ<br />考える</strong>
					<small>TAL / 2026</small>
				</div>
			</div>
			<div class="hero-art-rule"></div>
			<p class="hero-art-caption">CREATE<br />LEARN<br />THINK</p>
		</div>
	</section>

	<section id="books" class="section books-section" aria-labelledby="books-title">
		<div class="section-heading">
			<p class="eyebrow">PUBLICATIONS</p>
			<h2 id="books-title">書籍紹介</h2>
		</div>
		<div class="books-grid">
			{#each books as book, index (book.id)}
				<svelte:element this={book.url ? 'a' : 'article'} class="book-card" href={book.url || undefined}>
					{#if book.coverUrl}
						<img class="book-cover book-cover-image" src={book.coverUrl} alt={`${book.title}の表紙`} />
					{:else}
						<div class="book-cover" style:background-color={bookCoverColors[book.color] ?? book.color}>
							<span>VOL. {String(index + 1).padStart(2, '0')}</span>
							<strong>{book.title}</strong>
							<small>TECHNOLOGY<br />ACCELERATION<br />LAB</small>
						</div>
					{/if}
					<div class="book-details">
						<p class="book-category">{book.category}</p>
						<h3>{book.title}</h3>
						<p>{book.description}</p>
					</div>
				</svelte:element>
			{/each}
		</div>
	</section>

	<section id="members" class="section members-section" aria-labelledby="members-title">
		<div class="section-heading">
			<p class="eyebrow">MEMBERS</p>
			<h2 id="members-title">サークルメンバー</h2>
		</div>
		<div class="members-grid">
			{#each members as member (member.id)}
				<article class="member-card">
					{#if member.iconUrl}
						<img class="member-icon" src={`${base}${member.iconUrl}`} alt={`${member.name}のアイコン`} />
					{:else}
						<div class="member-initial" aria-hidden="true">{member.initial}</div>
					{/if}
					<div>
						<h3>{member.name}</h3>
						<p>得意分野<br />{member.role}</p>
						<div class="social-links">
							<a href={member.xUrl} rel="noreferrer" target="_blank">X</a>
							<a href={member.githubUrl} rel="noreferrer" target="_blank">GitHub</a>
						</div>
					</div>
				</article>
			{/each}
		</div>
	</section>

	<section id="events" class="section events-section" aria-labelledby="events-title">
		<div class="section-heading">
			<p class="eyebrow">EVENTS</p>
			<h2 id="events-title">出展イベント</h2>
		</div>
		<div class="events-list">
			{#each events as event (event.id)}
				<article class="event-row">
					<p class="event-date">{event.date}</p>
					<div class="event-body">
						<p class="event-status">{event.status}</p>
						<h3>{event.name}</h3>
						<p>{event.venue}</p>
					</div>
					{#if event.eventUrl}
						<a class="event-arrow" href={event.eventUrl} rel="noreferrer" target="_blank" aria-label={`${event.name}の詳細ページを開く`}>↗</a>
					{/if}
				</article>
			{/each}
		</div>
	</section>
</main>

<footer>
	<p>技術加速研究所</p>
	<p>TECHNOLOGY ACCELERATION LAB</p>
</footer>

<style>
	@import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Zen+Kaku+Gothic+New:wght@400;500;700;900&display=swap');

	:global(*) {
		box-sizing: border-box;
	}

	:global(html) {
		scroll-behavior: smooth;
	}

	:global(body) {
		margin: 0;
		background: #f5f2ea;
		color: #18211f;
		font-family: 'Zen Kaku Gothic New', sans-serif;
	}

	.site-header {
		align-items: center;
		background: rgba(245, 242, 234, 0.94);
		backdrop-filter: blur(12px);
		display: flex;
		inset: 0 0 auto;
		justify-content: space-between;
		margin: 0 auto;
		max-width: 1200px;
		padding: 22px 32px;
		position: fixed;
		width: 100%;
		z-index: 10;
	}

	.wordmark {
		align-items: center;
		color: inherit;
		display: inline-flex;
		font-size: 14px;
		font-weight: 700;
		gap: 10px;
		letter-spacing: 0.08em;
		text-decoration: none;
	}

	nav {
		display: flex;
		gap: 24px;
	}

	nav a {
		color: inherit;
		font-size: 13px;
		font-weight: 700;
		text-decoration: none;
	}

	nav a:hover,
	nav a:focus-visible,
	.hero-link:hover,
	.hero-link:focus-visible,
	.social-links a:hover,
	.social-links a:focus-visible {
		text-decoration: underline;
		text-decoration-thickness: 2px;
		text-underline-offset: 4px;
	}

	.hero {
		background: #143f3d;
		color: white;
		display: grid;
		grid-template-columns: minmax(0, 1.1fr) minmax(300px, 0.9fr);
		min-height: 570px;
		overflow: hidden;
		padding: 144px max(32px, calc((100vw - 1136px) / 2)) 72px;
	}

	.hero-copy {
		align-self: center;
		position: relative;
		z-index: 1;
	}

	.eyebrow {
		color: #e9573f;
		font-family: 'DM Mono', monospace;
		font-size: 12px;
		letter-spacing: 0.12em;
		margin: 0 0 16px;
	}

	.hero .eyebrow {
		color: #f6d95e;
	}

	h1,
	h2,
	h3,
	p {
		margin-top: 0;
	}

	h1 {
		font-size: clamp(42px, 6vw, 76px);
		font-weight: 900;
		letter-spacing: 0;
		line-height: 1.18;
		margin-bottom: 24px;
	}

	.hero-lead {
		font-size: 18px;
		font-weight: 500;
		line-height: 1.9;
		margin-bottom: 36px;
	}

	.hero-link {
		border-bottom: 2px solid #f6d95e;
		color: white;
		display: inline-flex;
		font-size: 14px;
		font-weight: 700;
		gap: 32px;
		padding: 10px 2px;
		text-decoration: none;
	}

	.hero-link span {
		font-size: 20px;
		line-height: 0.75;
	}

	.hero-art {
		align-self: center;
		aspect-ratio: 1;
		justify-self: center;
		max-width: 440px;
		position: relative;
		width: 100%;
	}

	.hero-art-label,
	.hero-art-caption {
		color: #f6d95e;
		font-family: 'DM Mono', monospace;
		font-size: 11px;
		letter-spacing: 0.08em;
		line-height: 1.5;
		margin: 0;
		position: absolute;
	}

	.hero-art-label {
		left: 2%;
		top: 5%;
	}

	.hero-art-caption {
		bottom: 6%;
		right: 0;
		text-align: right;
	}

	.book-stack {
		height: 76%;
		left: 10%;
		position: absolute;
		top: 12%;
		width: 74%;
	}

	.hero-book {
		box-shadow: 10px 12px 0 rgba(7, 25, 24, 0.28);
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding: 22px;
		position: absolute;
	}

	.hero-book-back {
		background: #9acfc7;
		color: #143f3d;
		height: 80%;
		left: 17%;
		top: 1%;
		transform: rotate(11deg);
		width: 60%;
	}

	.hero-book-middle {
		background: #f6d95e;
		color: #18211f;
		height: 84%;
		left: 9%;
		top: 7%;
		transform: rotate(-6deg);
		width: 63%;
	}

	.hero-book-back span,
	.hero-book-middle span,
	.hero-book-front small {
		font-family: 'DM Mono', monospace;
		font-size: 11px;
		letter-spacing: 0.07em;
		line-height: 1.45;
	}

	.hero-book-front {
		background: #e9573f;
		color: #fffaf0;
		height: 86%;
		left: 19%;
		top: 10%;
		transform: rotate(3deg);
		width: 64%;
	}

	.hero-book-front p {
		font-size: 12px;
		font-weight: 700;
		margin: 0;
	}

	.hero-book-front strong {
		font-size: clamp(28px, 4vw, 46px);
		font-weight: 900;
		line-height: 1.25;
	}

	.hero-art-rule {
		background: #f6d95e;
		height: 1px;
		position: absolute;
		right: -4%;
		top: 20%;
		width: 26%;
	}

	.section {
		margin: 0 auto;
		max-width: 1200px;
		padding: 112px 32px;
	}

	.section-heading {
		align-items: end;
		display: flex;
		justify-content: space-between;
		margin-bottom: 42px;
	}

	.section-heading .eyebrow {
		margin: 0;
	}

	h2 {
		font-size: clamp(30px, 4vw, 46px);
		font-weight: 900;
		letter-spacing: 0;
		margin: 0;
	}

	.books-section {
		border-bottom: 1px solid #c9c4b8;
	}

	.books-grid {
		display: grid;
		gap: 28px;
		grid-template-columns: repeat(3, minmax(0, 1fr));
	}

	.book-card {
		color: inherit;
		display: grid;
		gap: 20px;
		text-decoration: none;
	}

	.book-cover {
		aspect-ratio: 0.78;
		background: #e9573f;
		color: #18211f;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding: 24px;
		transition: transform 180ms ease;
	}

	.book-card:hover .book-cover {
		transform: translateY(-6px) rotate(-1deg);
	}

	.book-cover-image {
		object-fit: cover;
		padding: 0;
	}

	.book-cover span,
	.book-cover small {
		font-family: 'DM Mono', monospace;
		font-size: 11px;
		letter-spacing: 0.07em;
		line-height: 1.45;
	}

	.book-cover strong {
		font-size: clamp(24px, 3vw, 38px);
		font-weight: 900;
		line-height: 1.35;
	}

	.book-details h3,
	.member-card h3,
	.event-body h3 {
		font-size: 20px;
		font-weight: 700;
		margin-bottom: 8px;
	}

	.book-details > p:last-child,
	.member-card > div p,
	.event-body > p:last-child {
		color: #58615e;
		font-size: 14px;
		line-height: 1.8;
		margin-bottom: 0;
	}

	.book-category,
	.event-status {
		color: #e9573f;
		font-family: 'DM Mono', monospace;
		font-size: 11px;
		letter-spacing: 0.08em;
		margin-bottom: 10px;
	}

	.members-section {
		background: #e6e1d5;
		max-width: none;
		padding-left: max(32px, calc((100vw - 1136px) / 2));
		padding-right: max(32px, calc((100vw - 1136px) / 2));
	}

	.members-grid {
		display: grid;
		gap: 20px;
		grid-template-columns: repeat(3, minmax(0, 1fr));
	}

	.member-card {
		align-items: center;
		border-top: 3px solid #18211f;
		display: grid;
		gap: 18px;
		grid-template-columns: auto minmax(0, 1fr);
		padding-top: 20px;
	}

	.member-initial {
		align-items: center;
		background: #143f3d;
		border-radius: 50%;
		color: #f6d95e;
		display: flex;
		font-family: 'DM Mono', monospace;
		font-size: 23px;
		height: 68px;
		justify-content: center;
		width: 68px;
	}

	.member-icon {
		border-radius: 50%;
		display: block;
		height: 68px;
		object-fit: cover;
		width: 68px;
	}

	.social-links {
		display: flex;
		gap: 14px;
		margin-top: 14px;
	}

	.social-links a {
		color: #143f3d;
		font-family: 'DM Mono', monospace;
		font-size: 12px;
		text-decoration: none;
	}

	.events-section {
		padding-bottom: 128px;
	}

	.events-list {
		border-top: 1px solid #18211f;
	}

	.event-row {
		align-items: center;
		border-bottom: 1px solid #c9c4b8;
		display: grid;
		gap: 24px;
		grid-template-columns: 150px 1fr auto;
		padding: 26px 4px;
	}

	.event-date {
		font-family: 'DM Mono', monospace;
		font-size: 13px;
		margin: 0;
	}

	.event-body h3 {
		margin-bottom: 4px;
	}

	.event-status {
		margin-bottom: 6px;
	}

	.event-arrow {
		color: inherit;
		font-size: 26px;
		line-height: 1;
		text-decoration: none;
	}

	.event-arrow:hover,
	.event-arrow:focus-visible {
		color: #e9573f;
	}

	footer {
		align-items: center;
		background: #18211f;
		color: #f5f2ea;
		display: flex;
		font-family: 'DM Mono', monospace;
		font-size: 11px;
		justify-content: space-between;
		letter-spacing: 0.06em;
		padding: 24px max(32px, calc((100vw - 1136px) / 2));
	}

	footer p {
		margin: 0;
	}

	@media (max-width: 720px) {
		.site-header {
			padding: 18px 20px;
		}

		.wordmark {
			font-size: 12px;
			gap: 7px;
		}

		nav {
			gap: 13px;
		}

		nav a {
			font-size: 11px;
		}

		.hero {
			grid-template-columns: 1fr;
			min-height: auto;
			padding: 128px 24px 42px;
		}

		.hero-art {
			margin-top: 48px;
			max-width: 270px;
		}

		.section,
		.members-section {
			padding: 72px 20px;
		}

		.section-heading {
			align-items: start;
			flex-direction: column;
			gap: 10px;
			margin-bottom: 30px;
		}

		.books-grid,
		.members-grid {
			grid-template-columns: 1fr;
		}

		.books-grid {
			gap: 42px;
		}

		.book-card {
			grid-template-columns: minmax(130px, 0.7fr) 1fr;
		}

		.event-row {
			align-items: start;
			gap: 8px;
			grid-template-columns: 1fr auto;
		}

		.event-date {
			grid-column: 1 / -1;
		}

		.event-arrow {
			grid-column: 2;
			grid-row: 2;
		}

		footer {
			align-items: start;
			flex-direction: column;
			gap: 8px;
			padding: 24px 20px;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		:global(html) {
			scroll-behavior: auto;
		}

		.book-cover {
			transition: none;
		}
	}
</style>
