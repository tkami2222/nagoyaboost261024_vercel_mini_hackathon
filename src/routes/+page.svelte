<script lang="ts">
	interface Ingredient {
		id: string;
		name: string;
		emoji: string;
	}

	interface Recipe {
		title: string;
		usedIngredients: string[];
		time: string;
		description: string;
		steps: string[];
	}

	// 秋が旬の食材リスト（きのこを具体的に分類）
	const seasonalIngredients: Ingredient[] = [
		{ id: 'sanma', name: 'さんま', emoji: '🐟' },
		{ id: 'sake', name: '鮭', emoji: '🐟' },
		{ id: 'saba', name: '鯖', emoji: '🐟' },
		{ id: 'shiitake', name: 'しいたけ', emoji: '🍄' },
		{ id: 'shimeji', name: 'しめじ', emoji: '🍄' },
		{ id: 'eringi', name: 'エリンギ', emoji: '🍄' },
		{ id: 'maitake', name: '舞茸', emoji: '🍄' },
		{ id: 'matsutake', name: '松茸', emoji: '🌲' },
		{ id: 'satsumaimo', name: 'さつまいも', emoji: '🍠' },
		{ id: 'kabocha', name: 'かぼちゃ', emoji: '🎃' },
		{ id: 'satoimo', name: '里芋', emoji: '🥔' },
		{ id: 'kuri', name: '栗', emoji: '🌰' },
		{ id: 'renkon', name: 'れんこん', emoji: '🥔' },
		{ id: 'gobou', name: 'ごぼう', emoji: '🥕' },
		{ id: 'shungiku', name: '春菊', emoji: '🥬' },
		{ id: 'ginnan', name: 'ぎんなん', emoji: '🟢' },
		{ id: 'kaki', name: '柿', emoji: '🟠' },
		{ id: 'nashi', name: '梨', emoji: '🍐' },
		{ id: 'budou', name: 'ぶどう', emoji: '🍇' }
	];

	// 具体的なきのこを用いた秋のレシピデータベース
	const recipeDatabase: Recipe[] = [
		{
			title: '秋刀魚の塩焼き 香味おろし添え',
			usedIngredients: ['さんま'],
			time: '15分',
			description: '脂の乗ったさんまを香ばしく焼き上げ、大根おろしとすだちでさっぱりといただく定番の味。',
			steps: [
				'さんまに軽く塩を振り、10分ほど置いて水気を拭き取る。',
				'グリルまたは魚焼き器で両面がこんがりきつね色になるまで焼く。',
				'皿に盛り付け、大根おろしを添える。'
			]
		},
		{
			title: 'さんまの梅煮',
			usedIngredients: ['さんま', 'ごぼう'],
			time: '25分',
			description: '梅干しと一緒にさっぱりと煮込むことで、骨まで柔らかく食べられる秋の煮魚。',
			steps: [
				'さんまは頭と内臓を取り、半分に切る。ごぼうはささがきにする。',
				'鍋に水、酒、醤油、みりん、砂糖、梅干し、生姜を入れて煮立てる。',
				'さんまとごぼうを加え、落とし蓋をして弱火で20分ほどじっくり煮る。'
			]
		},
		{
			title: '秋鮭のちゃんちゃん焼き',
			usedIngredients: ['鮭', 'しめじ', 'かぼちゃ'],
			time: '20分',
			description: '北海道の郷土料理。味噌とバターのコクが鮭や野菜に絡む絶品メニュー。',
			steps: [
				'キャベツ、玉ねぎ、かぼちゃを食べやすい大きさに切る。',
				'ホットプレートまたはフライパンにバターを熱し、野菜と鮭を並べて蒸し焼きにする。',
				'味噌、みりん、砂糖、酒を合わせた合わせ調味料を回しかけ、全体を豪快に混ぜ合わせる。'
			]
		},
		{
			title: '鮭としめじの和風ホイル焼き',
			usedIngredients: ['鮭', 'しめじ'],
			time: '15分',
			description: '旨味が凝縮された鮭としめじをアルミホイルで包み、素材の味を閉じ込めたヘルシーメニュー。',
			steps: [
				'アルミホイルに薄切り玉ねぎ、鮭、ほぐしたしめじの順にのせる。',
				'酒と醤油をふりかけ、バターをのせてしっかりと包む。',
				'オーブントースターや魚焼きグリルで12〜15分加熱する。'
			]
		},
		{
			title: '秋鮭のクリームチャウダー',
			usedIngredients: ['鮭', 'かぼちゃ', 'れんこん'],
			time: '25分',
			description: '秋の味覚ゴロゴロ、心も体も温まる濃厚なミルクチャウダー。',
			steps: [
				'鮭は一口大に切って塩コショウを振り、かぼちゃとれんこんは食べやすい大きさに切る。',
				'バターで玉ねぎと根菜類を炒め、小麦粉を振り込んで馴染ませる。',
				'牛乳とコンソメを加えて煮込み、仕上げに鮭を入れて火を通す。'
			]
		},
		{
			title: '脂がのった鯖の味噌煮',
			usedIngredients: ['鯖', 'ごぼう'],
			time: '20分',
			description: '甘辛い味噌の風味と生姜の香りが食欲をそそる、ご飯が進む日本の伝統おかず。',
			steps: [
				'鯖の切り身に熱湯をかけ、冷水にとって霜降り（臭み取り）をする。',
				'鍋に水、酒、砂糖、醤油、生姜の千切りを入れて沸騰させる。',
				'鯖を並べ入れ、落とし蓋をして中火で15分ほど煮込む。'
			]
		},
		{
			title: '秋の味覚！3種きのこのバター醤油パスタ',
			usedIngredients: ['しめじ', 'エリンギ', '舞茸'],
			time: '12分',
			description: 'たっぷりのきのこをバターと醤油で香ばしく炒めた、風味がたまらない和風パスタ。',
			steps: [
				'パスタを茹で始める。',
				'フライパンにバターを熱し、食べやすくほぐしたしめじ、エリンギ、舞茸を強火で炒める。',
				'茹で上がったパスタと茹で汁、醤油を加えてさっと絡める。'
			]
		},
		{
			title: 'エリンギと豚肉の旨味たっぷりオイスター炒め',
			usedIngredients: ['エリンギ'],
			time: '10分',
			description: '食感の良いエリンギと豚肉をオイスターソースでコク深く仕上げた一品。',
			steps: [
				'エリンギは食べやすい短冊切りにし、豚肉は一口大に切る。',
				'フライパンにごま油を熱し、豚肉を炒めてからエリンギを加える。',
				'オイスターソース、醤油、酒を回し入れて手早く炒め合わせる。'
			]
		},
		{
			title: 'しいたけの肉詰めジューシー焼き',
			usedIngredients: ['しいたけ'],
			time: '15分',
			description: '肉汁としいたけの旨味が口いっぱいに広がる、お弁当にもおすすめのおかず。',
			steps: [
				'しいたけの軸を切り落とし、内側に薄く片栗粉を振る。',
				'豚ひき肉、みじん切り玉ねぎ、調味料を混ぜ合わせたタネをしいたけに詰める。',
				'肉の面から焼き、焼き色がついたら裏返して蓋をし、蒸し焼きにする。'
			]
		},
		{
			title: '舞茸と豚肉の旨味たっぷり炒め',
			usedIngredients: ['舞茸'],
			time: '10分',
			description: '舞茸から出る旨味エキスが豚肉にしっかり染み込んだ、お手軽スピードおかず。',
			steps: [
				'舞茸を食べやすい大きさに手で裂き、豚肉は一口大に切る。',
				'フライパンにごま油を熱し、豚肉の色が変わるまで炒める。',
				'舞茸を加えてしんなりするまで炒め、塩コショウと醤油で味を調える。'
			]
		},
		{
			title: '極上！松茸の土瓶蒸し風スープ',
			usedIngredients: ['松茸', 'しいたけ'],
			time: '15分',
			description: '贅沢な香りが広がる、おうちで料亭気分を味わえる上品なお吸い物。',
			steps: [
				'松茸としいたけの石づきを削ぎ落とし、薄切りにする。',
				'鍋に出汁、薄口醤油、酒、塩を入れて温める。',
				'きのこ類を入れてひと煮立ちさせ、三つ葉を添える。'
			]
		},
		{
			title: 'ホクホクさつまいみのハニーバター煮',
			usedIngredients: ['さつまいも'],
			time: '20分',
			description: 'さつまいもの自然な甘みにはちみつとバターが絡み合う、おやつにもぴったりな一品。',
			steps: [
				'さつまいもを一口大の乱切りにし、水にさらす。',
				'鍋にさつまいもとかぶるくらいの水、砂糖、バター、はちみつを入れて火にかける。',
				'柔らかくなるまで弱火でじっくり煮詰める。'
			]
		},
		{
			title: 'さつまいこと鶏肉の甘酢炒め',
			usedIngredients: ['さつまいも'],
			time: '20分',
			description: '素揚げしたさつまいもの甘みと、甘酢ダレが絡んだ鶏肉の相性が抜群。',
			steps: [
				'さつまいもは乱切りにしてレンジで軽く加熱し、鶏肉は一口大に切る。',
				'鶏肉を炒め、火が通ったらさつまいもを加える。',
				'醤油、酢、砂糖、ケチャップを合わせたタレを回し入れて絡める。'
			]
		},
		{
			title: 'かぼちゃのほっこりポタージュ',
			usedIngredients: ['かぼちゃ'],
			time: '25分',
			description: 'かぼちゃの甘みが優しく広がる、クリーミーで温まるスープ。',
			steps: [
				'かぼちゃの種とワタを取り、皮を適当に削ぎ落として一口大に切る。',
				'鍋にかぼちゃ、玉ねぎ、ひたひたの水をいれて柔らかくなるまで煮る。',
				'ミキサーで滑らかにしてから牛乳を加え、塩コショウで味を調える。'
			]
		},
		{
			title: 'かぼちゃとひき肉のそぼろ煮',
			usedIngredients: ['かぼちゃ'],
			time: '20分',
			description: 'お箸が止まらない、出汁を含んだほっこり優しいおふくろの味。',
			steps: [
				'かぼちゃを食べやすい大きさに切る。',
				'鍋に出汁、醤油、みりん、砂糖、ひき肉を入れて軽く煮立たせる。',
				'かぼちゃを加え、落とし蓋をして柔らかくなるまで煮込む。'
			]
		},
		{
			title: 'とろ〜り里芋のイカ煮っころがし',
			usedIngredients: ['里芋'],
			time: '25分',
			description: '里芋のねっとりした食感とイカの旨味が抜群に合う、秋の定番和食。',
			steps: [
				'里芋は皮をむいて塩もみし、ぬめりを洗い流す。イカは食べやすい大きさに切る。',
				'鍋に出汁、醤油、みりん、酒、砂糖を入れて里芋を柔らかくなるまで煮る。',
				'仕上げにイカを加え、さっと火を通す。'
			]
		},
		{
			title: '里芋のほっこり唐揚げ 香ばし醤油味',
			usedIngredients: ['里芋'],
			time: '20分',
			description: '外はカリッと、中はねっとり食感がたまらないおつまみにも最高の一品。',
			steps: [
				'里芋を柔らかくなるまで茹で、皮をむいて一口大に切る。',
				'ニンニク、生姜、醤油、酒を下味として里芋に染み込ませる。',
				'片栗粉をまぶし、きつね色になるまでカラッと揚げる。'
			]
		},
		{
			title: '栗おこわ風もちもち炊き込みご飯',
			usedIngredients: ['栗'],
			time: '45分',
			description: '秋の贅沢。栗の甘みとほくほく感がたまらない、お祝いの席にもぴったりのご飯。',
			steps: [
				'栗の鬼皮と渋皮をきれいに剥き、水にさらしておく。',
				'炊飯器にといだ米、酒、みりん、塩、出汁を入れる。',
				'栗をのせて通常通り炊き上げる。'
			]
		},
		{
			title: 'れんこんと豚肉の甘辛炒め',
			usedIngredients: ['れんこん', 'ごぼう'],
			time: '15分',
			description: 'シャキシャキのれんこんとジューシーな豚肉が甘辛いタレによく絡むご飯が進むおかず。',
			steps: [
				'れんこんは半月切り、ごぼうは乱切りにし、それぞれ水にさらす。',
				'豚肉の色が変わるまで炒め、水気を切った根菜類を加えてさらに炒める。',
				'醤油、みりん、酒、砂糖を合わせたタレを回し入れ、汁気がなくなるまで炒りつける。'
			]
		},
		{
			title: 'シャキシャキれんこんとツナの和風サラダ',
			usedIngredients: ['れんこん'],
			time: '10分',
			description: 'さっと茹でたれんこんの食感が楽しい、マヨネーズと醤油のコク旨サラダ。',
			steps: [
				'れんこんを薄いイチョウ切りにし、さっと熱湯で茹でて水気を切る。',
				'ボウルに油を切ったツナ、れんこん、マヨネーズ、醤油、すりごまを入れる。',
				'全体をよく和えて器に盛る。'
			]
		},
		{
			title: 'ごぼうと牛肉の香ばし甘辛炒め（きんぴら風）',
			usedIngredients: ['ごぼう'],
			time: '15分',
			description: '定番のきんぴらに牛肉の旨味が加わった、ボリューム満点のおかず。',
			steps: [
				'ごぼうはささがきにして水にさらす。',
				'ごま油で牛肉と水気を切ったごぼうをしっかりと炒め合わせる。',
				'砂糖、醤油、みりん、鷹の爪を加え、汁気が飛ぶまで炒める。'
			]
		},
		{
			title: '春菊と牛肉のすき煮風サラダ',
			usedIngredients: ['春菊'],
			time: '10分',
			description: '春菊の爽やかな香りと生食の食感を楽しめる、大人の和風サラダ。',
			steps: [
				'春菊の葉の部分を摘み、冷水にさらしてパリッとさせてから水気をしっかり切る。',
				'甘辛く炒めた牛肉と細切りにしたれんこんをトッピングする。',
				'醤油ベースのドレッシングをかけてさっと混ぜて食べる。'
			]
		},
		{
			title: 'もっちり香ばしいぎんなんの串焼き',
			usedIngredients: ['ぎんなん'],
			time: '10分',
			description: '秋の香りを楽しめる、居酒屋風のシンプルでおいしいおつまみ。',
			steps: [
				'ぎんなんの殻にペンチや専用の道具で軽くヒビを入れる。',
				'耐熱容器に入れてラップをし、電子レンジ（500W）で1分半ほど加熱する。',
				'薄皮をむいて竹串に刺し、塩を振る。'
			]
		},
		{
			title: '柿と生ハムのマスカルポーネ白和え',
			usedIngredients: ['柿'],
			time: '10分',
			description: '秋の果物「柿」を使った、ワインにもよく合うおしゃれな新感覚おつまみ。',
			steps: [
				'柿を一口大の角切りにする。',
				'豆腐、マスカルポーネチーズ、白味噌、少量の塩を滑らかになるまで混ぜ合わせる。',
				'柿とちぎった生ハムを和え衣で優しく和える。'
			]
		},
		{
			title: 'シャキシャキ梨と生ハムのサラダ',
			usedIngredients: ['梨'],
			time: '5分',
			description: 'みずみずしい梨の甘さと生ハムの塩気が絶妙にマッチする爽やかサラダ。',
			steps: [
				'梨の皮と芯を取り除き、薄切りにする。',
				'ベビーリーフとともに皿に盛り付け、生ハムを散らす。',
				'オリーブオイルとレモン汁、黒コショウを回しかける。'
			]
		},
		{
			title: 'ぶどうとモッツァレラチーズのフルーツカプレーゼ',
			usedIngredients: ['ぶどう'],
			time: '5分',
			description: 'みずみずしいぶどうの甘みとチーズの塩気が絶妙にマッチする爽やかサラダ。',
			steps: [
				'ぶどうを半分に切って種を取り除く。',
				'一口大のモッツァレラチーズと合わせる。',
				'オリーブオイル、レモン汁、塩、黒コショウを回しかける。'
			]
		}
	];

	let selectedIds = $state<string[]>([]);
	let currentRecipe = $state<Recipe | null>(null);
	let isGenerating = $state(false);

	function toggleIngredient(id: string) {
		if (selectedIds.includes(id)) {
			selectedIds = selectedIds.filter((item) => item !== id);
		} else {
			selectedIds = [...selectedIds, id];
		}
	}

	function selectAll() {
		selectedIds = seasonalIngredients.map((i) => i.id);
	}

	function clearSelection() {
		selectedIds = [];
		currentRecipe = null;
	}

	function suggestRecipe() {
		isGenerating = true;
		setTimeout(() => {
			const selectedNames = seasonalIngredients
				.filter((i) => selectedIds.includes(i.id))
				.map((i) => i.name);

			let matched = recipeDatabase.filter((recipe) =>
				recipe.usedIngredients.some((ing) => selectedNames.includes(ing))
			);

			if (matched.length === 0) {
				matched = recipeDatabase;
			}

			const randomIndex = Math.floor(Math.random() * matched.length);
			currentRecipe = matched[randomIndex];
			isGenerating = false;
		}, 400);
	}
</script>

<svelte:head>
	<title>秋の旬食材レシピ提案</title>
	<meta name="description" content="今が旬の秋の食材を選んで、おすすめのレシピをランダムで提案してもらうアプリ" />
</svelte:head>

<div class="container">
	<header>
		<h1>🍁 秋の旬食材レシピ提案</h1>
		<p class="subtitle">使いたい秋の食材を選んで、今日のメニューを決めましょう！</p>
	</header>

	<section class="selection-section">
		<div class="section-header">
			<h2>秋の旬食材を選ぶ <span class="badge">複数選択可</span></h2>
			<div class="actions">
				<button type="button" class="text-btn" onclick={selectAll}>すべて選択</button>
				<button type="button" class="text-btn" onclick={clearSelection}>クリア</button>
			</div>
		</div>

		<div class="ingredient-grid">
			{#each seasonalIngredients as item}
				{@const isSelected = selectedIds.includes(item.id)}
				<button
					type="button"
					class="ingredient-chip {isSelected ? 'selected' : ''}"
					onclick={() => toggleIngredient(item.id)}
				>
					<span class="emoji">{item.emoji}</span>
					<span class="name">{item.name}</span>
				</button>
			{/each}
		</div>

		<div class="cta-container">
			<button
				type="button"
				class="primary-btn"
				onclick={suggestRecipe}
				disabled={isGenerating}
			>
				{isGenerating ? '秋のレシピを考えています…' : 'この食材でレシピを提案してもらう'}
			</button>
		</div>
	</section>

	{#if currentRecipe}
		<section class="result-section">
			<div class="recipe-card">
				<div class="recipe-header">
					<span class="tag">おすすめの秋レシピ</span>
					<span class="time">⏱️ 調理時間: {currentRecipe.time}</span>
				</div>
				<h3>{currentRecipe.title}</h3>
				<p class="description">{currentRecipe.description}</p>
				
				<div class="ingredients-used">
					<strong>使われている秋の食材:</strong>
					<div class="tags">
						{#each currentRecipe.usedIngredients as ing}
							<span class="mini-tag">{ing}</span>
						{/each}
					</div>
				</div>

				<div class="steps">
					<h4>作り方</h4>
					<ol>
						{#each currentRecipe.steps as step}
							<li>{step}</li>
						{/each}
					</ol>
				</div>
			</div>
		</section>
	{/if}
</div>

<style>
	.container {
		max-width: 44rem;
		margin: 0 auto;
		padding: 2rem 1rem;
		font-family: system-ui, -apple-system, sans-serif;
		color: var(--fg);
	}

	header {
		text-align: center;
		margin-bottom: 2.5rem;
	}

	h1 {
		font-size: 1.8rem;
		margin: 0 0 0.5rem;
		color: var(--fg);
	}

	.subtitle {
		margin: 0;
		color: var(--muted);
		font-size: 0.95rem;
	}

	.selection-section {
		background: var(--surface);
		border: 1px solid var(--line);
		border-radius: 1rem;
		padding: 1.5rem;
		box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
	}

	.section-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 1rem;
	}

	.section-header h2 {
		font-size: 1.1rem;
		margin: 0;
		display: flex;
		align-items: center;
		gap: 0.5rem;
		color: var(--fg);
	}

	.badge {
		font-size: 0.7rem;
		background: var(--line);
		color: var(--fg);
		padding: 0.2rem 0.5rem;
		border-radius: 999px;
		font-weight: 600;
	}

	.actions {
		display: flex;
		gap: 0.75rem;
	}

	.text-btn {
		background: none;
		border: none;
		color: var(--accent);
		font-size: 0.85rem;
		font-weight: 600;
		cursor: pointer;
		padding: 0;
	}

	.text-btn:hover {
		text-decoration: underline;
	}

	.ingredient-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(95px, 1fr));
		gap: 0.75rem;
		margin-bottom: 1.5rem;
	}

	.ingredient-chip {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 0.75rem 0.5rem;
		background: var(--surface);
		border: 2px solid var(--line);
		border-radius: 0.75rem;
		cursor: pointer;
		transition: all 0.2s ease;
	}

	.ingredient-chip:hover {
		border-color: var(--accent);
	}

	.ingredient-chip.selected {
		background: var(--accent);
		border-color: var(--accent);
	}

	/* 食材名・絵文字が同化して見えない問題を修正（コントラストを確保） */
	.ingredient-chip .name {
		font-size: 0.85rem;
		font-weight: 700;
		color: var(--fg);
	}

	.ingredient-chip.selected .name,
	.ingredient-chip.selected .emoji {
		color: #ffffff;
	}

	.emoji {
		font-size: 1.5rem;
		margin-bottom: 0.25rem;
	}

	.cta-container {
		text-align: center;
	}

	.primary-btn {
		width: 100%;
		padding: 0.85rem 1.5rem;
		background: var(--accent);
		color: white;
		border: none;
		border-radius: 0.75rem;
		font-size: 1rem;
		font-weight: 600;
		cursor: pointer;
		transition: opacity 0.2s ease;
	}

	.primary-btn:hover:not(:disabled) {
		opacity: 0.9;
	}

	.primary-btn:disabled {
		opacity: 0.6;
		cursor: progress;
	}

	.result-section {
		margin-top: 2rem;
	}

	.recipe-card {
		background: var(--surface);
		border: 1px solid var(--line);
		border-radius: 1rem;
		padding: 1.75rem;
		box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
		border-left: 5px solid var(--accent);
	}

	.recipe-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 0.75rem;
	}

	.tag {
		background: var(--line);
		color: var(--fg);
		font-size: 0.75rem;
		font-weight: 600;
		padding: 0.25rem 0.6rem;
		border-radius: 999px;
	}

	.time {
		font-size: 0.85rem;
		color: var(--muted);
	}

	.recipe-card h3 {
		margin: 0 0 0.5rem;
		font-size: 1.4rem;
		color: var(--fg);
	}

	.description {
		margin: 0 0 1.25rem;
		color: var(--muted);
		font-size: 0.95rem;
		line-height: 1.5;
	}

	.ingredients-used {
		margin-bottom: 1.25rem;
		font-size: 0.9rem;
		color: var(--fg);
	}

	.tags {
		display: inline-flex;
		gap: 0.4rem;
		margin-left: 0.5rem;
		vertical-align: middle;
	}

	.mini-tag {
		background: var(--line);
		color: var(--fg);
		font-size: 0.75rem;
		font-weight: 600;
		padding: 0.1rem 0.5rem;
		border-radius: 0.25rem;
	}

	.steps {
		border-top: 1px solid var(--line);
		padding-top: 1rem;
	}

	.steps h4 {
		margin: 0 0 0.5rem;
		font-size: 1rem;
		color: var(--fg);
	}

	.steps ol {
		margin: 0;
		padding-left: 1.25rem;
		color: var(--muted);
		font-size: 0.9rem;
		line-height: 1.6;
	}

	.steps li {
		margin-bottom: 0.4rem;
	}
</style>
