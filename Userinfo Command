#Im Dev Portal Intents aktivieren beide HAKEN

import discord
from discord.ext import commands

client = commands.Bot(command_prefix='!', intents=discord.Intents.all())     <<<<<<<<<<<<<<<<command_prefix deine Prefix

@client.event
async def on_ready():
    print('Online!  {}'.format(client.user.name))
    client.loop.create_task(status_task())


async def status_task():
    while True:
        await client.change_presence(activity=discord.Game('https://discord.gg/enN2U9G'), status=discord.Status.online)
        await asyncio.sleep(5)

        await client.change_presence(activity=discord.Game('Developer rivonivo (Simon)#1738'),
                                     status=discord.Status.online)
        await asyncio.sleep(5)#
        
       
@client.command()
@commands.has_permissions()
async def userinfo(ctx, member: discord.Member):
    em = discord.Embed(title=f'Dies ist eine Userinfo für {member.display_name}',
                       color=0x22a7f0)

    em.add_field(name='Server beigetreten',
                    value=member.joined_at.strftime('%d/%m/%Y, %H:%M:%S'),
                    inline=True)

    em.add_field(name='Discord beigetreten',
                    value=member.created_at.strftime('%d/%m/%Y, %H:%M:%S'),
                    inline=True)
    rollen = ''
    for role in member.roles:
        if not role.is_default():
            rollen += '{} \r\n'.format(role.mention)
    if rollen:
        em.add_field(name='Rollen', value=rollen, inline=True)
    em.set_thumbnail(url=member.avatar_url)
    em.set_footer(text='Userinfo')
    await ctx.send(embed=em)
    
    client.run('TOKEN')

