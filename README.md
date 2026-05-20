# 365bet-landing-page
import React, { useEffect, useState } from "react";
import { motion } from "framer-motion";
import {
  ChevronRight,
  Home,
  Trophy,
  Dice5,
  Fish,
  Gift,
  Crown,
  Send,
  MessageCircle,
  Gamepad2,
  Menu,
  X,
  Wallet,
  ShieldCheck,
  RotateCcw,
  CalendarCheck,
  Headphones,
  CircleDollarSign,
  Sparkles,
  Volume2,
} from "lucide-react";

export function formatMoney(value) {
  return `$${Number(value).toLocaleString(undefined, {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  })}`;
}

// Lightweight runtime checks for the money formatter.
// These do not affect the UI and help catch formatting regressions during development.
if (typeof window !== "undefined") {
  console.assert(formatMoney(0).startsWith("$"), "formatMoney should include a dollar sign");
  console.assert(formatMoney(1234.5).includes("1,234.50"), "formatMoney should format decimals and separators");
}

const navItems = [
  { label: "HOME", icon: Home, desc: "Back to the main 365BET landing page with premium neon casino style." },
  { label: "SPORTS", icon: Trophy, desc: "Sports betting zone for football, basketball, Snooker and live match entertainment." },
  { label: "LIVE CASINO", icon: Dice5, desc: "Live dealer casino area with table games, VIP rooms and real-time casino experience." },
  { label: "SLOTS", icon: Gamepad2, desc: "Slot game lobby with jackpot games, free spin rewards and popular providers." },
  { label: "FISHING", icon: Fish, desc: "Arcade fish shooting game section with fast action and mega win style gameplay." },
  { label: "LOTTERY", icon: Gift, desc: "Lottery and lucky number section for number games, draws and special prizes." },
  { label: "ESPORTS", icon: Gamepad2, desc: "Esports entertainment zone for competitive games and live gaming events." },
  { label: "PROMOTION", icon: Gift, desc: "Promotion page for welcome bonus, daily bonus, rebate, free spin and seasonal rewards." },
  { label: "VIP CLUB", icon: Crown, desc: "VIP member club with exclusive rewards, higher rebate, birthday bonus and priority support." },
];

const sideMenu = [
  { title: "VIP", icon: Crown },
  { title: "REBATE", icon: CircleDollarSign },
  { title: "FREE SPIN", icon: Dice5 },
  { title: "GIFT", icon: Gift },
];

const games = [
  {
    title: "SPORTS BETTING",
    desc: "Bet on Your Favorite Sports & Events",
    bg: "from-sky-950 via-blue-950 to-black",
    emoji: "⚽",
    image: "https://images.unsplash.com/photo-1574629810360-7efbbe195018?auto=format&fit=crop&w=1400&q=80",
  },
  {
    title: "LIVE CASINO",
    desc: "Real Dealer Real Experience",
    bg: "from-fuchsia-950 via-violet-950 to-black",
    emoji: "🃏",
    image: "https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=1200&q=80",
  },
  {
    title: "SLOTS",
    desc: "Hundreds of Exciting Slots",
    bg: "from-amber-950 via-red-950 to-black",
    emoji: "🎰",
    image: "https://images.unsplash.com/photo-1596838132731-3301c3fd4317?auto=format&fit=crop&w=1200&q=80",
  },
  {
    title: "FISHING",
    desc: "Arcade Fish Shooting Mega Win",
    bg: "from-cyan-950 via-blue-950 to-black",
    emoji: "🔫",
    image: "https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=1400&q=80",
  },
  {
    title: "LOTTERY",
    desc: "Lucky Numbers & Massive Lottery Prizes",
    bg: "from-purple-950 via-fuchsia-950 to-black",
    emoji: "🎟️",
    image: "https://images.unsplash.com/photo-1520583457224-aee11bad5112?auto=format&fit=crop&w=1400&q=80",
  },
];

const quickActions = [
  { title: "DEPOSIT", desc: "Fast & Secure", icon: Wallet },
  { title: "WITHDRAW", desc: "Instant Payout", icon: ShieldCheck },
  { title: "REBATE", desc: "Up to 5%", icon: RotateCcw },
  { title: "VIP CLUB", desc: "Exclusive Rewards", icon: Crown },
  { title: "DAILY CHECK-IN", desc: "Get Free Bonus", icon: CalendarCheck },
  { title: "LUCKY SPIN", desc: "Spin & Win", icon: Sparkles },
];

const HERO_BANNERS = [
  "https://static.gwvkyk.com/media/e41e960073f96d1bd6492.png",
  "https://static.gwvkyk.com/media/e41e960073f96d1bd6492.png",
  "https://static.gwvkyk.com/media/e41e960073f96d1bd6492.png",
  "https://static.gwvkyk.com/media/e41e960073f96d1bd6492.png",
]; // Put all hero banners inside /public folder.

const providers = [
  ["FAST DEPOSIT", 23456789.01],
  ["JILI", 15678901.23],
  ["JDB", 11234567.89],
  ["CQ9", 8765432.12],
  ["PRAGMATIC PLAY", 7654321.23],
];

function Header() {
  const [open, setOpen] = useState(false);
  const [showLogin, setShowLogin] = useState(false);

  return (
    <header className="sticky top-0 z-50 border-b border-violet-500/30 bg-[#050510]/90 backdrop-blur-2xl">
      <div className="mx-auto flex max-w-[1560px] items-center justify-between px-4 py-2">
        <div className="ml-6 text-3xl font-black italic tracking-tight text-white drop-shadow-[0_0_18px_rgba(99,102,241,1)] md:ml-10 md:text-4xl">
          365<span className="text-violet-300">BET</span>
        </div>

        <nav className="hidden items-center gap-6 xl:flex">
          {navItems.map(({ label, icon: Icon, desc }) => (
            <button key={label}  className="group relative flex min-w-16 flex-col items-center gap-1 rounded-xl px-3 py-2 text-[11px] font-black text-slate-200 transition hover:bg-violet-600/25 hover:text-cyan-200">
              <Icon className="h-5 w-5 group-hover:text-cyan-300" />
              {label}
            </button>
          ))}
        </nav>

        <div className="hidden items-center gap-3 md:flex">
          <a
            href="https://wa.me/60123456789"
            target="_blank"
            rel="noreferrer"
            className="relative z-20 inline-flex cursor-pointer items-center justify-center rounded-xl border border-cyan-300/40 bg-cyan-400/10 px-6 py-2 text-sm font-black tracking-wide text-cyan-100 shadow-[0_0_18px_rgba(34,211,238,.35)] backdrop-blur-xl transition hover:scale-105 hover:bg-cyan-400/20 hover:shadow-[0_0_28px_rgba(34,211,238,.65)]"
          >
            LOGIN
          </a>

          <a
            href="https://wa.me/60123456789"
            target="_blank"
            rel="noreferrer"
            className="relative z-20 inline-flex cursor-pointer items-center justify-center rounded-xl bg-gradient-to-r from-fuchsia-600 via-violet-600 to-cyan-500 px-7 py-2.5 text-sm font-black tracking-wide text-white shadow-[0_0_24px_rgba(217,70,239,.65)] transition hover:scale-105 hover:shadow-[0_0_38px_rgba(34,211,238,.75)]"
          >
            JOIN NOW
          </a>
        </div>

        <button onClick={() => setOpen(!open)} className="text-white xl:hidden">{open ? <X /> : <Menu />}</button>
      </div>

      {showLogin && (
        <div className="fixed inset-0 z-[100] grid place-items-center bg-black/70 p-4 backdrop-blur-md">
          <motion.div
            initial={{ opacity: 0, scale: 0.9, y: 20 }}
            animate={{ opacity: 1, scale: 1, y: 0 }}
            className="relative w-full max-w-md overflow-hidden rounded-[2rem] border border-cyan-400/30 bg-[#09091b]/95 p-7 shadow-[0_0_60px_rgba(34,211,238,.35)]"
          >
            <button
              onClick={() => setShowLogin(false)}
              className="absolute right-4 top-4 rounded-full border border-white/10 bg-white/5 p-2 text-white"
            >
              <X className="h-5 w-5" />
            </button>

            <div className="mb-6 text-center">
              <div className="text-sm font-black tracking-[.35em] text-cyan-200">MEMBER LOGIN</div>
              <h2 className="mt-2 text-4xl font-black italic text-white">
                365<span className="text-violet-300">BET</span>
              </h2>
            </div>

            <div className="space-y-4">
              <input
                placeholder="Username"
                className="w-full rounded-2xl border border-cyan-400/20 bg-white/5 px-5 py-4 text-white outline-none placeholder:text-slate-500"
              />

              <input
                type="password"
                placeholder="Password"
                className="w-full rounded-2xl border border-cyan-400/20 bg-white/5 px-5 py-4 text-white outline-none placeholder:text-slate-500"
              />

              <button className="w-full rounded-2xl bg-gradient-to-r from-cyan-500 to-violet-600 py-4 text-sm font-black tracking-[.2em] text-white shadow-[0_0_28px_rgba(34,211,238,.45)]">
                LOGIN NOW
              </button>
            </div>

            <div className="mt-5 flex items-center justify-between text-xs font-bold text-slate-400">
              <span>Fast Withdraw</span>
              <span>VIP Rewards</span>
              <span>5% Rebate</span>
            </div>
          </motion.div>
        </div>
      )}

      {open && (
        <div className="grid grid-cols-2 gap-2 border-t border-violet-500/20 bg-[#09091b] p-4 xl:hidden">
          {navItems.map(({ label, icon: Icon }) => (
            <button key={label} className="flex items-center gap-2 rounded-xl border border-violet-500/20 bg-white/5 p-3 text-sm font-bold text-white">
              <Icon className="h-5 w-5 text-cyan-300" /> {label}
            </button>
          ))}
        </div>
      )}
    </header>
  );
}

function LeftSideMenu() {
  return (
    <div className="fixed left-2 top-44 z-40 hidden w-20 flex-col gap-2 lg:flex">
      {sideMenu.map(({ title, icon: Icon, hot }) => (
        <button key={title} className="relative rounded-2xl border border-violet-500/60 bg-[#10082c]/75 p-3 text-center shadow-[0_0_22px_rgba(124,58,237,.45)] backdrop-blur-xl transition hover:scale-105 hover:border-cyan-300">
          {hot && <span className="absolute -right-1 top-2 rounded-full bg-red-500 px-1.5 text-[9px] font-black text-white">HOT</span>}
          <Icon className="mx-auto h-7 w-7 text-violet-100 drop-shadow-[0_0_12px_rgba(217,70,239,.9)]" />
          <div className="mt-1 text-[11px] font-black text-white">{title}</div>
        </button>
      ))}
    </div>
  );
}

function FloatingContact() {
  return (
    <div className="fixed right-3 top-1/2 z-50 flex -translate-y-1/2 flex-col gap-3 sm:right-5">
      
      <motion.a
        animate={{
          scale: [1, 1.08, 1],
          boxShadow: [
            "0 0 20px rgba(34,211,238,.45)",
            "0 0 38px rgba(34,211,238,.95)",
            "0 0 20px rgba(34,211,238,.45)",
          ],
        }}
        transition={{ duration: 1.6, repeat: Infinity }}
        href="https://t.me/yourtelegram"
        target="_blank"
        rel="noreferrer"
        className="relative overflow-hidden rounded-2xl border border-cyan-400/60 bg-cyan-500/20 p-3 text-center backdrop-blur-xl transition hover:scale-110"
      >
        <motion.div
          animate={{ x: ["-120%", "220%"] }}
          transition={{ duration: 2.2, repeat: Infinity, ease: "linear" }}
          className="pointer-events-none absolute inset-y-0 w-1/2 bg-gradient-to-r from-transparent via-white/25 to-transparent blur-lg"
        />
        <Send className="mx-auto h-7 w-7 text-cyan-100" />
        <div className="mt-1 text-[10px] font-bold text-white">TELEGRAM</div>
      </motion.a>
      <motion.a
        animate={{
          scale: [1, 1.08, 1],
          boxShadow: [
            "0 0 20px rgba(74,222,128,.45)",
            "0 0 38px rgba(74,222,128,.95)",
            "0 0 20px rgba(74,222,128,.45)",
          ],
        }}
        transition={{ duration: 1.6, repeat: Infinity, delay: .4 }}
        href="https://wa.me/60123456789" target="_blank" rel="noreferrer" className="relative overflow-hidden rounded-2xl border border-green-400/60 bg-green-500/20 p-3 text-center backdrop-blur-xl transition hover:scale-110">
        <motion.div
          animate={{ x: ["-120%", "220%"] }}
          transition={{ duration: 2.2, repeat: Infinity, ease: "linear" }}
          className="pointer-events-none absolute inset-y-0 w-1/2 bg-gradient-to-r from-transparent via-white/25 to-transparent blur-lg"
        />
        <MessageCircle className="mx-auto h-7 w-7 text-green-100" />
        <div className="mt-1 text-[10px] font-bold text-white">WHATSAPP</div>
      </motion.a>
    </div>
  );
}

function Hero() {
  const [currentBanner, setCurrentBanner] = useState(0);

  useEffect(() => {
    const bannerInterval = setInterval(() => {
      setCurrentBanner((prev) => (prev + 1) % HERO_BANNERS.length);
    }, 4500);

    return () => clearInterval(bannerInterval);
  }, []);

  return (
    <section className="relative overflow-hidden border-b border-violet-500/40 bg-[#020208] px-4 pb-5 pt-3 shadow-[0_0_70px_rgba(124,58,237,.45)]">
      <div className="relative mx-auto mb-3 flex max-w-[1500px] items-center overflow-hidden rounded-xl border border-violet-500/40 bg-violet-950/30 px-4 py-2 text-sm font-bold text-violet-100 shadow-[0_0_20px_rgba(124,58,237,.35)] backdrop-blur-xl">
        <motion.div
          animate={{ x: ["-100%", "220%"] }}
          transition={{ duration: 4.5, repeat: Infinity, ease: "linear" }}
          className="pointer-events-none absolute inset-y-0 w-1/3 bg-gradient-to-r from-transparent via-white/20 to-transparent blur-xl"
        />

        <motion.div
          animate={{ x: [0, -1200] }}
          transition={{ duration: 18, repeat: Infinity, ease: "linear" }}
          className="flex min-w-max items-center gap-10 whitespace-nowrap"
        >
          <span className="text-sm font-black tracking-wide text-violet-100 drop-shadow-[0_0_12px_rgba(167,139,250,.85)]">
            🎉 Welcome to 365BET — Best Online Casino & Sports Betting Platform!
          </span>

          <span className="text-sm font-black tracking-wide text-cyan-100 drop-shadow-[0_0_12px_rgba(34,211,238,.85)]">
            🔥 Daily Bonus • Weekly Rebate • VIP Reward • 24/7 Customer Support
          </span>

          <span className="text-sm font-black tracking-wide text-yellow-200 drop-shadow-[0_0_12px_rgba(250,204,21,.85)]">
            💎 Instant Withdraw • Fast Deposit • Unlimited Winning
          </span>

          <span className="text-sm font-black tracking-wide text-fuchsia-200 drop-shadow-[0_0_12px_rgba(217,70,239,.85)]">
            🚀 Join Now & Claim Your Exclusive Welcome Bonus Today!
          </span>
        </motion.div>

        <Volume2 className="absolute right-4 h-4 w-4 text-cyan-200" />
      </div>

      <div className="mx-auto max-w-[1500px]">
        <div
          className="relative min-h-[520px] overflow-hidden rounded-[2rem] border border-violet-500/40 bg-cover bg-center shadow-[0_0_65px_rgba(124,58,237,.55)]"
          style={{ backgroundImage: `url(${HERO_BANNERS[currentBanner]})` }}
        >
          <div className="absolute inset-0 bg-gradient-to-b from-black/10 via-transparent to-black/30" />
          <motion.div animate={{ x: ["-35%", "125%"] }} transition={{ duration: 6.5, repeat: Infinity, ease: "linear" }} className="pointer-events-none absolute top-0 h-full w-1/3 bg-gradient-to-r from-transparent via-white/10 to-transparent blur-xl" />

          <div className="absolute bottom-5 left-1/2 z-20 flex -translate-x-1/2 gap-2">
            {HERO_BANNERS.map((_, index) => (
              <button
                key={index}
                onClick={() => setCurrentBanner(index)}
                className={`h-2.5 rounded-full transition-all duration-300 ${
                  currentBanner === index
                    ? "w-10 bg-cyan-300 shadow-[0_0_18px_rgba(34,211,238,.95)]"
                    : "w-2.5 bg-white/40"
                }`}
              />
            ))}
          </div>

          <div className="absolute left-6 bottom-6 hidden rounded-2xl border border-fuchsia-400/50 bg-black/45 px-6 py-4 shadow-[0_0_25px_rgba(217,70,239,.45)] backdrop-blur-xl md:block">
            <div className="text-xl font-black text-fuchsia-200">♣ LIVE CASINO</div>
            <div className="mt-1 text-sm font-bold text-white">Real Dealer<br />Real Experience</div>
          </div>

          <div className="absolute right-6 bottom-6 hidden rounded-2xl border border-yellow-300/50 bg-black/45 px-6 py-4 shadow-[0_0_25px_rgba(250,204,21,.45)] backdrop-blur-xl md:block">
            <div className="text-xl font-black text-yellow-200">👑 VIP EXCLUSIVE</div>
            <div className="mt-1 text-sm font-bold text-white">High Rewards<br />More Benefits</div>
          </div>
        </div>
      </div>
    </section>
  );
}

function WinnerTicker() {
  const randomGames = [
    "JILI",
    "PRAGMATIC PLAY",
    "CQ9",
    "JDB",
    "LIVE CASINO",
    "SPORTS BETTING",
    "SLOTS",
  ];

  const [winners, setWinners] = useState([]);

  useEffect(() => {
    const generateWinner = () => {
      const firstDigit = Math.random() > 0.5 ? "8" : "9";
      const visibleDigits = Array.from({ length: 3 }, () => Math.floor(Math.random() * 10)).join("");
      const phone = `+65 ${firstDigit}${visibleDigits} ****`;
      const game = randomGames[Math.floor(Math.random() * randomGames.length)];
      const amount = Math.floor(Math.random() * 25000 + 3000).toLocaleString();

      return `${phone} won $${amount} on ${game}`;
    };

    setWinners(Array.from({ length: 12 }, generateWinner));

    const interval = setInterval(() => {
      setWinners(Array.from({ length: 12 }, generateWinner));
    }, 7000);

    return () => clearInterval(interval);
  }, []);

  return (
    <section className="mx-auto max-w-[1500px] px-4 pt-4">
      <div className="relative overflow-hidden rounded-2xl border border-yellow-300/20 bg-gradient-to-r from-yellow-500/10 via-black to-yellow-500/10 px-5 py-3 shadow-[0_0_25px_rgba(250,204,21,.15)]">
        <motion.div
          animate={{ x: [0, -1800] }}
          transition={{ duration: 22, repeat: Infinity, ease: "linear" }}
          className="flex min-w-max items-center gap-12 whitespace-nowrap"
        >
          {winners.map((winner, index) => (
            <div
              key={index}
              className="flex items-center gap-3 text-sm font-black text-yellow-100"
            >
              <span className="text-green-400">●</span>
              {winner}
              <ChevronRight className="h-4 w-4 text-yellow-300" />
            </div>
          ))}
        </motion.div>
      </div>
    </section>
  );
}

function Jackpot() {
  const [jackpot, setJackpot] = useState(88888888.88);
  const [fastDeposit, setFastDeposit] = useState(23456789.01);
  const [jiliAmount, setJiliAmount] = useState(15678901.23);
  const [pragmaticAmount, setPragmaticAmount] = useState(7654321.23);
  const [jdbAmount, setJdbAmount] = useState(11234567.89);
  const [cq9Amount, setCq9Amount] = useState(8765432.12);

  useEffect(() => {
    const jackpotInterval = setInterval(() => {
      setJackpot((prev) => prev + Math.random() * 88);
    }, 120);

    const depositInterval = setInterval(() => {
      setFastDeposit((prev) => prev + Math.random() * 25);
    }, 180);

    const jiliInterval = setInterval(() => {
      setJiliAmount((prev) => prev + Math.random() * 18);
    }, 220);

    const pragmaticInterval = setInterval(() => {
      setPragmaticAmount((prev) => prev + Math.random() * 14);
    }, 260);

    const jdbInterval = setInterval(() => {
      setJdbAmount((prev) => prev + Math.random() * 16);
    }, 210);

    const cq9Interval = setInterval(() => {
      setCq9Amount((prev) => prev + Math.random() * 12);
    }, 240);

    return () => {
      clearInterval(jackpotInterval);
      clearInterval(depositInterval);
      clearInterval(jiliInterval);
      clearInterval(pragmaticInterval);
      clearInterval(jdbInterval);
      clearInterval(cq9Interval);
    };
  }, []);

  return (
    <section className="mx-auto -mt-1 max-w-[1500px] px-4">
      <div className="grid gap-2 rounded-2xl border border-fuchsia-500/50 bg-[#08051d]/95 p-2 shadow-[0_0_32px_rgba(217,70,239,.35)] lg:grid-cols-[1.5fr_repeat(5,1fr)]">
        <div className="relative overflow-hidden rounded-xl border border-fuchsia-500/30 bg-gradient-to-r from-violet-950 via-black to-violet-950 p-4 shadow-[inset_0_0_30px_rgba(217,70,239,.18)]">
          <motion.div animate={{ x: ["-35%", "120%"] }} transition={{ duration: 3.5, repeat: Infinity, ease: "linear" }} className="pointer-events-none absolute top-0 h-full w-1/3 bg-gradient-to-r from-transparent via-white/15 to-transparent blur-xl" />

          <div className="text-sm font-black tracking-[.22em] text-yellow-300">PROGRESSIVE JACKPOT</div>

          <motion.div animate={{ scale: [1, 1.03, 1] }} transition={{ duration: 1.7, repeat: Infinity }} className="mt-2 text-3xl font-black tracking-wide text-yellow-200 drop-shadow-[0_0_16px_rgba(250,204,21,.95)] md:text-4xl">
            {formatMoney(jackpot)}
          </motion.div>

          <div className="mt-2 flex items-center gap-2 text-xs font-bold text-yellow-100/80">
            <span className="animate-pulse text-green-400">●</span>
            LIVE WIN UPDATE
          </div>
        </div>

        {providers.map(([name, baseAmount], index) => {
          let displayAmount = baseAmount;

          if (index === 0) {
            displayAmount = fastDeposit;
          }

          if (index === 1) {
            displayAmount = jiliAmount;
          }

          if (index === 2) {
            displayAmount = jdbAmount;
          }

          if (index === 3) {
            displayAmount = cq9Amount;
          }

          if (index === 4) {
            displayAmount = pragmaticAmount;
          }

          return (
            <motion.div
              whileHover={{ y: -3, scale: 1.02 }}
              key={name}
              className="rounded-xl border border-violet-500/25 bg-white/5 p-4 shadow-[inset_0_0_24px_rgba(124,58,237,.15)] backdrop-blur-xl"
            >
              <div className="text-xs font-black text-white">{name}</div>
              <div className="mt-2 font-black text-yellow-200 drop-shadow-[0_0_10px_rgba(250,204,21,.55)]">
                {formatMoney(displayAmount)}
              </div>
            </motion.div>
          );
        })}
      </div>
    </section>
  );
}

function GameGrid() {
  return (
    <main className="mx-auto max-w-[1500px] px-4 py-5">
      <div className="mb-4 flex items-end justify-between">
        <div>
          <div className="text-sm font-black tracking-[.35em] text-cyan-200 drop-shadow-[0_0_12px_rgba(34,211,238,.9)]">PREMIUM GAME LOBBY</div>
          <h2 className="mt-1 text-3xl font-black italic text-white md:text-4xl">Choose Your Game</h2>
        </div>
        <div className="hidden rounded-full border border-fuchsia-400/40 bg-fuchsia-500/10 px-5 py-2 text-xs font-black text-fuchsia-100 shadow-[0_0_22px_rgba(217,70,239,.35)] backdrop-blur-xl md:block">
          HOT GAMES • FAST ACCESS
        </div>
      </div>

      <div className="grid gap-4 md:grid-cols-2 xl:grid-cols-5">
        {games.map((game, index) => (
          <motion.div
            initial={{ opacity: 0, y: 24 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: index * 0.08 }}
            whileHover={{ y: -10, scale: 1.025 }}
            key={game.title}
            
            className={`group relative min-h-[255px] overflow-hidden rounded-[1.7rem] border border-cyan-300/40 bg-gradient-to-br ${game.bg} shadow-[0_0_30px_rgba(34,211,238,.22)] ring-1 ring-white/10`}
          >
            <img src={game.image} alt={game.title} className="absolute inset-0 h-full w-full object-cover opacity-70 saturate-150 transition duration-700 group-hover:scale-110 group-hover:opacity-85" />

            <div className="absolute inset-0 bg-gradient-to-t from-black via-black/60 to-black/5" />
            <div className="absolute inset-0 bg-[radial-gradient(circle_at_75%_18%,rgba(255,255,255,.22),transparent_24%),radial-gradient(circle_at_20%_80%,rgba(34,211,238,.2),transparent_35%)]" />
            <motion.div animate={{ x: ["-45%", "135%"] }} transition={{ duration: 4.8 + index * 0.3, repeat: Infinity, ease: "linear" }} className="pointer-events-none absolute top-0 h-full w-1/2 bg-gradient-to-r from-transparent via-white/12 to-transparent blur-xl" />

            <div className="absolute left-4 top-4 rounded-full border border-white/20 bg-black/45 px-3 py-1 text-[10px] font-black tracking-[.18em] text-cyan-100 shadow-[0_0_16px_rgba(34,211,238,.35)] backdrop-blur-xl">
              #{String(index + 1).padStart(2, "0")} HOT
            </div>

            <motion.div animate={{ y: [0, -10, 0], rotate: [-4, 4, -4] }} transition={{ duration: 3 + index * 0.25, repeat: Infinity }} className="absolute -right-4 bottom-8 text-8xl opacity-90 drop-shadow-[0_0_24px_rgba(255,255,255,.55)]">
              {game.emoji}
            </motion.div>

            <div className="absolute bottom-0 left-0 right-0 p-5">
              <h3 className="text-2xl font-black text-cyan-100 drop-shadow-[0_0_14px_rgba(34,211,238,1)]">{game.title}</h3>
              <p className="mt-2 max-w-[220px] text-sm font-semibold text-white/90">{game.desc}</p>
            </div>
          </motion.div>
        ))}
      </div>

      <div className="mt-5 grid gap-3 md:grid-cols-3 xl:grid-cols-6">
        {quickActions.map(({ title, desc, icon: Icon }) => (
          <motion.div whileHover={{ y: -5, scale: 1.02 }} key={title} className="group relative overflow-hidden rounded-2xl border border-violet-500/40 bg-violet-950/30 p-5 shadow-[0_0_22px_rgba(124,58,237,.25)] backdrop-blur-xl">
            <div className="absolute inset-0 bg-gradient-to-br from-white/10 via-transparent to-fuchsia-500/10 opacity-0 transition group-hover:opacity-100" />
            <div className="relative flex items-center gap-4">
              <div className="grid h-12 w-12 place-items-center rounded-2xl border border-violet-300/40 bg-violet-500/20 shadow-[0_0_18px_rgba(167,139,250,.35)]">
                <Icon className="h-7 w-7 text-violet-100 drop-shadow-[0_0_12px_rgba(167,139,250,.9)]" />
              </div>
              <div>
                <div className="font-black text-white">{title}</div>
                <div className="text-sm text-slate-300">{desc}</div>
              </div>
            </div>
          </motion.div>
        ))}
      </div>
    </main>
  );
}

function SimpleInfoSections() {
  return (
    <section className="mx-auto max-w-[1500px] px-4 pb-8">
      <div className="relative overflow-hidden rounded-[2.4rem] border border-violet-500/35 bg-[#08051d]/80 p-6 shadow-[0_0_55px_rgba(124,58,237,.32)] backdrop-blur-2xl">
        <div className="pointer-events-none absolute -left-24 top-10 h-72 w-72 rounded-full bg-cyan-400/10 blur-3xl" />
        <div className="pointer-events-none absolute -right-24 bottom-10 h-72 w-72 rounded-full bg-fuchsia-500/10 blur-3xl" />
        <motion.div
          animate={{ x: ["-40%", "130%"] }}
          transition={{ duration: 6.5, repeat: Infinity, ease: "linear" }}
          className="pointer-events-none absolute inset-y-0 w-1/3 bg-gradient-to-r from-transparent via-white/8 to-transparent blur-2xl"
        />

        <div className="relative mb-7 flex flex-col items-center justify-between gap-4 text-center md:flex-row md:text-left">
          <div>
            <div className="text-sm font-black tracking-[.38em] text-cyan-200 drop-shadow-[0_0_12px_rgba(34,211,238,.9)]">
              GAME INFORMATION
            </div>
            <h2 className="mt-2 bg-gradient-to-r from-white via-cyan-100 to-fuchsia-200 bg-clip-text text-3xl font-black italic text-transparent md:text-5xl">
              Premium Entertainment Categories
            </h2>
            <p className="mt-3 max-w-2xl text-sm font-semibold leading-6 text-slate-300">
              Explore each 365BET section with a clean, high-end neon category guide.
            </p>
          </div>

          <div className="rounded-full border border-yellow-300/35 bg-yellow-400/10 px-5 py-2 text-xs font-black tracking-[.2em] text-yellow-100 shadow-[0_0_22px_rgba(250,204,21,.25)]">
            FAST ACCESS • VIP STYLE
          </div>
        </div>

        <div className="relative grid gap-4 md:grid-cols-2 xl:grid-cols-4">
          {navItems.slice(1).map(({ label, desc, icon: Icon }, index) => (
            <motion.div
              key={label}
              initial={{ opacity: 0, y: 18 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ delay: index * 0.04 }}
              whileHover={{ y: -8, scale: 1.015 }}
              className="group relative overflow-hidden rounded-[1.6rem] border border-cyan-400/25 bg-gradient-to-br from-white/10 via-violet-950/35 to-black/30 p-5 shadow-[0_0_24px_rgba(34,211,238,.13)]"
            >
              <div className="absolute inset-0 bg-gradient-to-br from-cyan-400/10 via-transparent to-fuchsia-500/10 opacity-0 transition duration-300 group-hover:opacity-100" />
              <div className="absolute -right-6 -top-6 text-7xl font-black text-white/5 transition group-hover:text-white/10">
                {String(index + 1).padStart(2, "0")}
              </div>

              <div className="relative flex items-center gap-3">
                <div className="grid h-14 w-14 place-items-center rounded-2xl border border-cyan-300/35 bg-cyan-400/10 shadow-[0_0_22px_rgba(34,211,238,.2)] transition group-hover:scale-110 group-hover:bg-cyan-400/20">
                  <Icon className="h-7 w-7 text-cyan-100 drop-shadow-[0_0_12px_rgba(34,211,238,.8)]" />
                </div>

                <div>
                  <div className="text-lg font-black text-cyan-100 drop-shadow-[0_0_10px_rgba(34,211,238,.65)]">
                    {label}
                  </div>
                  <div className="mt-1 h-0.5 w-14 rounded-full bg-gradient-to-r from-cyan-300 to-fuchsia-400" />
                </div>
              </div>

              <p className="relative mt-4 text-sm font-medium leading-6 text-slate-300">
                {desc}
              </p>

              <div className="relative mt-5 flex items-center justify-between text-xs font-black text-white/80">
                <span className="rounded-full border border-white/10 bg-white/5 px-3 py-1">DETAILS</span>
                <span className="text-cyan-200 transition group-hover:translate-x-1">MORE →</span>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
}

export default function App() {
  useEffect(() => {
    document.body.style.background = "#020208";
  }, []);

  return (
    <div className="min-h-screen overflow-x-hidden bg-[#020208] text-white">
      <div className="pointer-events-none fixed inset-0 bg-[radial-gradient(circle_at_20%_10%,rgba(124,58,237,.28),transparent_28%),radial-gradient(circle_at_80%_30%,rgba(34,211,238,.18),transparent_28%),radial-gradient(circle_at_50%_90%,rgba(217,70,239,.18),transparent_30%)]" />
      <Header />
      <LeftSideMenu />
      <Hero />
      <WinnerTicker />
      <Jackpot />
      <GameGrid />
      <SimpleInfoSections />
      <FloatingContact />
      <footer className="border-t border-violet-500/20 py-8 text-center text-sm text-slate-400">
        ©365BET 2026 Singapore.All Rights Reserved.
      </footer>
    </div>
  );
}
