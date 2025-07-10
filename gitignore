require('dotenv').config();
const { Telegraf } = require('telegraf');

const bot = new Telegraf(process.env.BOT_TOKEN);

// Welcome message and start command
bot.start((ctx) => {
  const welcomeMessage = `🌟 Welcome to Our Airdrop Bot! 🌟

To participate in the airdrop, please complete these simple steps:

1. Join our Telegram channel: [Channel Link]
2. Join our Telegram group: [Group Link]
3. Follow us on Twitter: [Twitter Link]
4. Submit your Solana wallet address

Click /submit to submit your wallet address after completing the steps above.`;

  ctx.reply(welcomeMessage);
});

// Submit wallet command
bot.command('submit', (ctx) => {
  ctx.reply('Please enter your Solana wallet address:');
});

// Handle wallet address submission
bot.on('text', (ctx) => {
  const message = ctx.message.text;
  
  // Simple check if it might be a Solana address (basic validation)
  if (message.length >= 32 && message.length <= 44) {
    ctx.reply(`🎉 Congratulations! 10 SOL is on its way to your wallet (${message}). Thank you for participating!`);
    
    // In a real bot, you would store this address somewhere
    console.log(`New submission: ${message}`);
  } else {
    ctx.reply('This doesn\'t look like a valid Solana wallet address. Please try again or use /submit to start over.');
  }
});

// Launch bot
bot.launch()
  .then(() => console.log('Bot started successfully'))
  .catch(err => console.error('Error starting bot:', err));

// Enable graceful stop
process.once('SIGINT', () => bot.stop('SIGINT'));
process.once('SIGTERM', () => bot.stop('SIGTERM'));
