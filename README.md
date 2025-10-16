import { Telegraf } from "telegraf";
import fetch from "node-fetch";

const BOT_TOKEN = "YOUR_TELEGRAM_BOT_TOKEN"; // এখানেই তোমার Telegram bot token বসাও
const ADSTERRA_TOKEN = "YOUR_ADSTERRA_API_TOKEN"; // এখানেই Adsterra token বসাও

const bot = new Telegraf(BOT_TOKEN);

bot.start((ctx) => {
  ctx.reply("👋 স্বাগতম! /stats লিখলে তোমার Adsterra earnings দেখতে পারবে।");
});

bot.command("stats", async (ctx) => {
  await ctx.reply("⏳ ডেটা আনছি, একটু অপেক্ষা করো...");

  try {
    const response = await fetch("https://api.adsterra.com/v2/stats", {
      method: "GET",
      headers: {
        Authorization: `Bearer ${ADSTERRA_TOKEN}`,
        Accept: "application/json",
      },
    });

    if (!response.ok) throw new Error("Adsterra API error!");

    const data = await response.json();

    // নিচে response data format অনুযায়ী সাজাও
    const clicks = data.clicks ?? "N/A";
    const impressions = data.impressions ?? "N/A";
    const revenue = data.revenue ?? "N/A";

    ctx.reply(
      `📊 *Adsterra Stats*\n\n🖱 Clicks: ${clicks}\n👁 Impressions: ${impressions}\n💰 Revenue: ${revenue}`,
      { parse_mode: "Markdown" }
    );
  } catch (error) {
    ctx.reply("⚠️ ডেটা আনতে সমস্যা হয়েছে! টোকেন বা নেটওয়ার্ক চেক করো।");
  }
});

bot.launch();
console.log("🚀 Bot is running...");
