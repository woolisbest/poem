import React, { useState, useEffect } from "react";
import { motion } from "framer-motion";
import { Copy, Share2, Heart, Download } from "lucide-react";

// 恥ずかしいポエムメーカー - Single-file React component
// Tailwind CSS utility classes are used for styling (no imports needed here).
// Features:
// - ランダム生成（カテゴリー・強さ・長さを指定可能）
// - お気に入り保存（localStorage）
// - コピー・共有・ダウンロード
// - アニメーション

// 外部ファイルから読み込むため、配列は削除
let POEMS = [];

export default function EmbarrassingPoemMaker() {
  const categories = ["すべて", ...Array.from(new Set(POEMS.map((p) => p.category)))]
  const [category, setCategory] = useState("すべて");
  const [intensity, setIntensity] = useState(1);
  const [lengthPref, setLengthPref] = useState("any"); // any, short, long
  const [poem, setPoem] = useState(null);
  const [favorites, setFavorites] = useState([]);
  const [history, setHistory] = useState([]);

  useEffect(() => {
    // お気に入りと履歴のロード
    const saved = localStorage.getItem("epm_favs");
    if (saved) setFavorites(JSON.parse(saved));
    const hist = localStorage.getItem("epm_hist");
    if (hist) setHistory(JSON.parse(hist));

    // date.json の読み込み
    fetch("date.json")
      .then(res => res.json())
      .then(data => {
        POEMS = data;
      })
      .catch(() => console.error("date.json の読み込みに失敗しました"));
  }, []);

  useEffect(() => {
    localStorage.setItem("epm_favs", JSON.stringify(favorites));
  }, [favorites]);

  useEffect(() => {
    localStorage.setItem("epm_hist", JSON.stringify(history));
  }, [history]);

  function filterPool() {
    return POEMS.filter(p => {
      if (category !== "すべて" && p.category !== category) return false;
      if (p.intensity > intensity) return false;
      if (lengthPref !== "any" && p.length !== lengthPref) return false;
      return true;
    });
  }

  function generate() {
    const pool = filterPool();
    if (pool.length === 0) {
      setPoem({ text: "該当するポエムが見つかりませんでした。設定を変えてみてください。" });
      return;
    }
    const pick = pool[Math.floor(Math.random() * pool.length)];
    setPoem(pick);
    const newHist = [pick, ...history].slice(0, 50);
    setHistory(newHist);
  }

  function toggleFav(p) {
    const key = p.text;
    if (favorites.some(f => f.text === key)) {
      setFavorites(favorites.filter(f => f.text !== key));
    } else {
      setFavorites([p, ...favorites]);
    }
  }

  function copyPoem(p) {
    navigator.clipboard.writeText(p.text).then(() => {
      alert("ポエムをコピーしました！");
    }).catch(() => alert("コピーに失敗しました。"));
  }

  function sharePoem(p) {
    if (navigator.share) {
      navigator.share({ title: "恥ずかしいポエム", text: p.text }).catch(() => {});
    } else {
      copyPoem(p);
      alert("共有機能が使えないためコピーしました。");
    }
  }

  function downloadPoem(p) {
    const blob = new Blob([p.text], { type: "text/plain;charset=utf-8" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = "poem.txt";
    document.body.appendChild(a);
    a.click();
    a.remove();
    URL.revokeObjectURL(url);
  }

  return (
    <div className="min-h-screen bg-gradient-to-br from-rose-50 to-amber-50 p-6 flex flex-col items-center">
      <div className="w-full max-w-3xl">
        <header className="flex items-center justify-between mb-6">
          <div>
            <h1 className="text-2xl font-extrabold">恥ずかしいポエムメーカー</h1>
            <p className="text-sm text-gray-600">ランダムに羞恥度高めのポエムを出します。設定を変えて変態（※良い意味）を調整しよう。</p>
          </div>
          <div className="flex gap-2 items-center">
            <button onClick={() => { setCategory("すべて"); setIntensity(10); setLengthPref("any"); generate(); }} className="px-3 py-1 rounded-lg bg-white shadow">おまかせ一発</button>
            <button onClick={() => { setCategory("すべて"); setIntensity(1); setLengthPref("any"); generate(); }} className="px-3 py-1 rounded-lg bg-white shadow">ライト版</button>
          </div>
        </header>

        <main className="mb-6">
          <div className="bg-white p-4 rounded-2xl shadow-md">
            <div className="grid grid-cols-1 md:grid-cols-3 gap-3 mb-4">
              <div>
                <label className="text-xs">カテゴリ</label>
                <select value={category} onChange={(e) => setCategory(e.target.value)} className="w-full mt-1 p-2 rounded border">
                  {categories.map(c => <option key={c} value={c}>{c}</option>)}
                </select>
              </div>
              <div>
                <label className="text-xs">羞恥度（高いほど恥ずかしい）: {intensity}</label>
                <input type="range" min={1} max={10} value={intensity} onChange={(e) => setIntensity(Number(e.target.value))} className="w-full mt-1" />
              </div>
              <div>
                <label className="text-xs">長さ</label>
                <select value={lengthPref} onChange={(e) => setLengthPref(e.target.value)} className="w-full mt-1 p-2 rounded border">
                  <option value="any">どれでも</option>
                  <option value="short">短文</option>
                  <option value="long">長文</option>
                </select>
              </div>
            </div>

            <div className="flex gap-3">
              <button onClick={generate} className="flex-1 py-3 rounded-lg bg-gradient-to-r from-pink-400 to-orange-400 text-white font-semibold shadow-lg">ポエムを出す</button>
              <button onClick={() => { const p = { text: "手動で挿入したサンプルポエム。" }; setPoem(p); }} className="px-4 py-3 rounded-lg bg-white border">サンプル</button>
            </div>
          </div>

          <section className="mt-6">
            <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} className="bg-white p-6 rounded-2xl shadow-lg">
              {!poem ? (
                <div className="text-center text-gray-500">まだポエムがありません。「ポエムを出す」を押してみてください。</div>
              ) : (
                <div>
                  <div className="flex items-start justify-between">
                    <div className="text-sm text-gray-500">カテゴリ: {poem.category || "-"} ／ 称度: {poem.intensity || "-"}</div>
                    <div className="flex gap-2">
                      <button onClick={() => toggleFav(poem)} title="お気に入り" className="p-2 rounded hover:bg-gray-100">
                        <Heart size={18} />
                      </button>
                      <button onClick={() => copyPoem(poem)} title="コピー" className="p-2 rounded hover:bg-gray-100">
                        <Copy size={18} />
                      </button>
                      <button onClick={() => sharePoem(poem)} title="共有" className="p-2 rounded hover:bg-gray-100">
                        <Share2 size={18} />
                      </button>
                      <button onClick={() => downloadPoem(poem)} title="ダウンロード" className="p-2 rounded hover:bg-gray-100">
                        <Download size={18} />
                      </button>
                    </div>
                  </div>

                  <div className="mt-4 whitespace-pre-wrap text-lg leading-relaxed">{poem.text}</div>

                  <div className="mt-4 text-right text-xs text-gray-400">(ここに表示されるポエムはランダム生成されたサンプルです)</div>
                </div>
              )}
            </motion.div>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-4 mt-4">
              <div className="bg-white p-4 rounded-lg shadow">
                <h3 className="font-semibold mb-2">履歴</h3>
                {history.length === 0 ? <div className="text-sm text-gray-400">まだ履歴はありません。</div> : (
                  <ul className="space-y-2 max-h-48 overflow-auto text-sm">
                    {history.map((h, i) => (
                      <li key={i} className="flex justify-between items-start">
                        <div className="truncate">{h.text}</div>
                        <div className="flex gap-2">
                          <button onClick={() => { setPoem(h); }} className="px-2">開く</button>
                          <button onClick={() => toggleFav(h)} className="px-2">☆</button>
                        </div>
                      </li>
                    ))}
                  </ul>
                )}
              </div>

              <div className="bg-white p-4 rounded-lg shadow">
                <h3 className="font-semibold mb-2">お気に入り</h3>
                {favorites.length === 0 ? <div className="text-sm text-gray-400">お気に入りはまだありません。</div> : (
                  <ul className="space-y-2 max-h-48 overflow-auto text-sm">
                    {favorites.map((f, i) => (
                      <li key={i} className="flex justify-between items-start">
                        <div className="truncate">{f.text}</div>
                        <div className="flex gap-2">
                          <button onClick={() => { setPoem(f); }} className="px-2">開く</button>
                          <button onClick={() => toggleFav(f)} className="px-2">削除</button>
                        </div>
                      </li>
                    ))}
                  </ul>
                )}
              </div>
            </div>
          </section>
        </main>

        <footer className="text-center text-sm text-gray-500 mt-6">
          <div>Made with ❤️ — カスタマイズしたい場合は教えてください。</div>
        </footer>
      </div>
    </div>
  );
}
