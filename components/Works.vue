<template>
  <v-container class="works-wrapper">
    <v-row>
      <v-col cols="12">
        <p class="text-left text-h2" id="works">Works</p>
      </v-col>
      <v-col cols="12">
        <p class="text-left text-h4">Sounds</p>
        <p class="text-left">
          映像・アニメ、ショー、バンドレコーディングで携わった作品を紹介します。
        </p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="4" v-for="card in cards" :key="card.title">
        <v-card class="mx-auto" max-width="500">
          <v-img
            v-if="card.type == 'music'"
            class="white--text align-end"
            height="300px"
            :src="card.src"
          >
            <audio :src="card.sound" controls />
          </v-img>
          <v-card-actions height="300px" v-else-if="card.type == 'video'">
            <video
              width="100%"
              :src="card.video"
              :poster="card.poster"
              controls
            />
          </v-card-actions>
          <v-card-actions v-else-if="card.type == 'youtube'">
            <youtube ref="youtube" :video-id="card.videoId" height="300px" />
          </v-card-actions>
          <v-card-title class="text-left" v-text="card.title"></v-card-title>
          <v-card-subtitle
            class="text-left"
            v-text="card.year"
          ></v-card-subtitle>
          <v-card-text
            class="text-left text--primary"
            v-text="card.desc"
          ></v-card-text>
          <v-divider class="mt-2 mx-4"></v-divider>
          <v-card-text class="text-left">
            <v-chip
              class="mr-2 mb-2 pa-2"
              v-for="tag in card.tags"
              :key="tag"
              >{{ tag }}</v-chip
            >
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <p class="text-left text-h4 mt-6">Songs</p>
        <p class="text-left">個人的に制作した楽曲を紹介します。</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="4" v-for="song in songs" :key="song.title">
        <v-card class="mx-auto" max-width="500">
          <v-card-actions>
            <youtube ref="youtube" :video-id="song.videoId" height="300px" />
          </v-card-actions>
          <v-card-title class="text-left" v-text="song.title"></v-card-title>
          <v-card-text
            class="text-left text--primary"
            v-text="song.desc"
          ></v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <p class="text-left text-h4 mt-6">Applications</p>
        <p class="text-left">個人的に制作したWebアプリ・サイトを紹介します。</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="4" v-for="app in applications" :key="app.title">
        <v-card class="mx-auto" max-width="500">
          <v-img class="white--text align-end" height="300px" :src="app.src" />
          <v-card-title class="text-left" v-text="app.title"></v-card-title>
          <v-card-text
            class="text-left text--primary"
            v-text="app.desc"
          ></v-card-text>
          <v-card-actions>
            <v-btn text color="#F75940" link nuxt :href="app.url" target='_blank'>
              Webサイトへ
            </v-btn>
          </v-card-actions>
          <v-divider class="mt-2 mx-4"></v-divider>
          <v-card-text class="text-left">
            <v-chip class="mr-2 mb-2 pa-2" v-for="tag in app.tags" :key="tag">{{
              tag
            }}</v-chip>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <p class="text-left text-h4 mt-6">Research</p>
        <p class="text-left">大学院時代の研究を紹介します。</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="4">
        <v-card class="mx-auto" max-width="500">
          <v-img class="white--text align-end" height="300px" src="/research.png" />
          <v-card-title class="text-left">「EVらしい」音デザイン指針の構築</v-card-title>
          <v-card-text
            class="text-left text--primary"
          >自動車メーカーとの共同研究により電気自動車の音デザインを2年間研究しました。電気自動車という「未知なる音」を視覚的な印象からアプローチし、デザイナーによる感覚的な音デザインではなくエンジニアが体系的にデザインできる指針を構築しました。2年間で音響学会4回、国際学会1回の計5回の学会発表を経験しました。</v-card-text>
          <v-card-actions>
            <v-btn text color="#F75940" link nuxt href="https://drive.google.com/file/d/1lzR_Ht-M0loOCpFOKPQqFqLocwMuzAOx/view" target='_blank'>
              全文
            </v-btn>
            <v-btn text color="#F75940" link nuxt href="https://drive.google.com/file/d/1LVLvef19DzfXu8Qu0qGaUiQhBLu6Cyy0/view?usp=sharing" target='_blank'>
              要旨
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style>
.works-wrapper {
  text-align: center;
  padding: 0 0 20vh 0;
}
.v-card__subtitle,
.v-card__text {
  font-size: 1rem;
}
</style>

<script>
import Vue from "vue";
import VueYoutube from "vue-youtube";

Vue.use(VueYoutube);

export default {
  name: "Works",
  data: () => ({
    cards: [
      {
        title: "ヤサイピーマンズ 1st Album「ヤサイピーマンズ1」",
        type: "music",
        year: "2020",
        src: "/yasai.jpg",
        sound: "/anomachihe.mp3",
        desc:
          "自身のオリジナルバンドの1stアルバムをレコーディングからミキシング/マスタリングまでを手掛けました。ほぼすべての曲の作詞作曲も担当しています。bandcampの他、各種ストリーミングサービスでも配信予定です。",
        tags: [
          "スタジオレコーディング",
          "ミキシング/マスタリング",
          "作詞",
          "楽曲制作",
          "ボーカル",
          "ギター"
        ]
      },
      {
        title: "MOJIBAKE 1st Single「Broken Metronome」",
        type: "music",
        year: "2019",
        src: "/mojibake.jpg",
        sound: "/Broken_Metronome.mp3",
        desc:
          "福岡で活動しているスリーピースバンド「MOJIBAKE」のファーストシングル「Broken Metronome」と他4曲のミキシング/マスタリングを担当しました。",
        tags: ["ミキシング/マスタリング"]
      },
      {
        title: "製菓会社様向けアニメーション",
        type: "video",
        year: "2019",
        video: "/kanro.mp4",
        poster: "/kanro.png",
        desc: "カンロ株式会社様向けアニメーションの楽曲制作を担当しました。",
        tags: ["楽曲制作", "SE制作", "フィールドレコーディング"]
      },
      {
        title: "おといろこなた",
        type: "youtube",
        year: "2018",
        videoId: "H7qFTWXNq7c",
        desc:
          "イラストレーター/アニメーター酒井進也氏の自主制作アニメ「おといろこなた」の音響、楽曲制作を担当しました。「音」をモチーフにしたアニメーションのため、作中で用いられている全てのSEをフォーリーおよびフィールドレコーディングをおこない作成しました。",
        tags: [
          "フォーリー",
          "フィールドレコーディング",
          "ミキシング/マスタリング",
          "SE制作",
          "楽曲制作"
        ]
      },
      {
        title: "Cait Sith Sessions 1st E.P.「Seamlog」",
        type: "music",
        year: "2017",
        src: "/3824.jpg",
        sound: "/cait.mp3",
        desc:
          "ケルト音楽バンドのスタジオレコーディングおよびミキシング/マスタリングを担当しました。ヴァイオリン×2、チェロ、フルート、ギター、パーカッションのバンド形態でセッション形式のレコーディングをおこないました。",
        tags: ["スタジオレコーディング", "ミキシング/マスタリング"]
      },
      {
        title: "PANX公演「IRIS」",
        type: "youtube",
        year: "2015",
        videoId: "sSg_UZnJW_A",
        desc:
          "演劇と巨大プロジェクションマッピングのコラボレーション企画のサウンディレクションの副担当とエンディング楽曲制作の担当をしました。建物に囲まれた環境のリバーブを考慮・活用したミックスをおこないました。",
        tags: ["サウンドディレクション", "楽曲制作"]
      },
      {
        title: "CBA project 14",
        type: "youtube",
        year: "2014",
        videoId: "DwLwbSgDDtQ",
        desc:
          "ファッションショーサークルの音効総指揮として、各曲のディレクション、サラウンドミックス、エンドロール作曲を担当しました。5.1chに天井音を加えた「5.1.1ch」サラウンドシステムを採用しました。天井音も追加したサラウンドの効果により、左右だけでなく高さも意識させ、舞台全体の立体感を表現することができました。",
        tags: [
          "ミキシング/マスタリング",
          "サウンドディレクション",
          "楽曲制作",
          "SE制作"
        ]
      },
      {
        title: "ロトスコ",
        type: "youtube",
        year: "2014",
        videoId: "MkroPSknOWQ",
        desc:
          "映像制作団体Moveのロトスコープ（実写映像をベースにしてアニメーション映像を作り上げる技法）を用いたショートムービーの楽曲制作を担当しました。",
        tags: ["楽曲制作"]
      },
      {
        title: "ぶたに小判-Eating is Living-",
        type: "youtube",
        year: "2013",
        videoId: "TiaGk44_-1U",
        desc:
          "映像制作団体Moveのコマ撮りを用いたショートムービーの楽曲制作を担当しました。",
        tags: ["楽曲制作"]
      }
    ],
    songs: [
      {
        title: "HIIT timer",
        videoId: "iAnor21Krw8",
        desc:
          "20秒+10秒休憩×8ラウンドのトレーニング「タバタ式トレーニング」を曲に合わせながら楽曲として作成しました。"
      },
      {
        title: "ソースをかけて召し上がれッ♪",
        videoId: "XReWCHkN6Xw",
        desc:
          "「広島風お好み焼き屋の看板娘が繰り広げるドタバタラブコメ」アニメのOP曲をコンセプトに制作した楽曲です。複数回の転調により曲の疾走感を生み出しました。"
      },
      {
        title: "働き方改革の曲",
        videoId: "j2gf3Oa8d-8",
        desc:
          "会社の働き方改革事務局から依頼を受けて作成した楽曲です。近未来をコンセプトにオートチューンを駆使した楽曲です。"
      },
      {
        title: "Just",
        videoId: "46LmEMUOW-k",
        desc: "EDMをテーマにメロディーの心地よさを重視して作成した楽曲です"
      },
      {
        title: "Tom's Bots",
        videoId: "wYULcRXPTKU",
        desc:
          "「トムとジェリー」が駆け巡っているかのような疾走感をコンセプトに制作した楽曲です。"
      },
      {
        title: "ステイ・ウィズ・ミー",
        videoId: "H43TQIwomrs",
        desc: "パンクロックをコンセプトに宅録制作した楽曲です。"
      },
      {
        title: "Raindrops",
        videoId: "nbMYTHSyGBE",
        desc: "雨粒をモチーフにした楽曲です。"
      }
    ],
    applications: [
      {
        title: "Sound Generator",
        url: "https://sound-generator-5cd79.web.app/",
        src: "/soundGenerator.png",
        desc:
          "「音響の初学者が音の仕組みを身をもって体験できる」をコンセプトに、正弦波・矩形波などの単純な波形を組み合わせたときにどのような波形になるかを可視化するために構築しました。Web Audio APIを用いて、音の生成、波形表示、音の合成を構築しました。",
        tags: ["Nuxt.js", "Web Audio API", "Firebase"]
      },
      {
        title: "ポートフォリオサイト",
        url: "https://katsuyayamagata-portfolio.web.app/",
        src: "/portfolio.png",
        desc: "本ポートフォリオサイトはNuxtJSで構築しました。",
        tags: ["Nuxt.js"]
      }
    ]
  }),
  computed: {
    player() {
      return this.$refs.youtube.player;
    }
  },
  methods: {
    playVideo() {
      this.$refs.youtube.player.playVideo();
    }
  }
};
</script>
