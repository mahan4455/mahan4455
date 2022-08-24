const {
	isAdmin,
	sleep,
	bot,
	numToJid,
	jidToNum,
	formatTime,
} = require('../lib/')
const fm = true

bot(
	{
		pattern: 'سیک ?(.*)',
		fromMe: fm,
		desc: 'Remove members from Group by 𝐷𝛥𝛤𝛫.',
		type: 'group',
		onlyGroup: true,
	},
	async (message, match) => {
                try{
		const participants = await message.groupMetadata(message.jid)
		const isImAdmin = await isAdmin(participants, message.client.user.jid)
		if (!isImAdmin) return await message.sendMessage(`_I'm not admin._`)
		let user =
			message.mention[0] ||
			message.reply_message.jid ||
			(match == 'all' && match)
		if (!user) return await message.sendMessage(`_Give me a user_`)
		if (user == 'all') {
			user = participants
				.filter((member) => !member.admin == true)
				.map(({ id }) => id)
			await message.sendMessage(
				`_kicking everyone(${user.length})_\n*Restart bot if u wanna stop.*`
			)
			await sleep(10 * 1000)
		}
		return await message.Kick(user)}catch(e){ message.sendMessage(`${e}`)};
	}
)
