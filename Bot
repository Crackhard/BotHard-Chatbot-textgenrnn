from textgenrnn import textgenrnn
import discord
import asyncio
from discord.ext import commands
from collections import defaultdict
import random
import time
textgen = textgenrnn()
bot = commands.Bot(command_prefix='++')
TOKEN = 'token goes here'
prefix = '++'

client = discord.Client()
@client.event
async def on_message(message):
    try:
        start_time = time.time()
        if message.author != client.user:
            if not message.content.startswith('=='):
                if len(message.content) < 1024:
                    if message.channel.id == '498332532702445579' or message.channel.id == '502254053397626891' or message.channel.id == '502718705122279424':
                        await asyncio.sleep(1)
                        f = open('Database.txt', 'a')
                        f.write(f'{message.content}\n')
                        await client.send_typing(message.channel)
                        textgen.train_from_file('Database.txt', num_epochs=1)
                        fmt = textgen.generate(1, temperature=0.7, return_as_list=True)
                        await client.send_message(message.channel, str(fmt).replace("'",'').replace('[', '').replace(']','') + '\n')
                        with open('Responses.txt', 'a') as ine:
                            ine.write(f'{fmt}\n')
                        with open('Database.txt', 'r+') as f:
                            f.readline()
                            data = f.read()
                            f.seek(0)
                            f.write(data)
                            f.truncate()
                            with open("Database.txt") as fp:
                                for i, line in enumerate(fp):
                                    if i == 6:
                                        lines = fp.readlines()
                                        lines = lines[:-1]
                                        break
                        print("--- %s seconds ---" % (time.time() - start_time))
                else:
                    await client.send_message(message.channel, 'The message exceeds the limit')
            elif message.content.startswith('==Clear'):
                if author.id == '399392841308045312':
                    open("Database.txt", "w").close()
                    await client.send_message(message.channel, 'Learning database cleared')
                else:
                    await client.send_message(message.channel, "You are not Crackhard, cease.")
                    return
            elif message.content.startswith('==555'):
                print(message.author)
                if author.id == '399392841308045312':
                    await client.send_message(message.channel, 'Time to roast kids')
                else:
                    await client.send_message(message.channel, "You are not Crackhard, cease.")
                    return
            else:
                return
    except (UnicodeEncodeError, AssertionError):
        if message.author != client.user:
            textgen.train_from_file('Database.txt', num_epochs=1)
            fmt = textgen.generate(1, temperature=0.5, return_as_list=True)
            await client.send_message(message.channel, str(fmt).replace("'",'').replace('[', '').replace(']','') + '\n')
            with open('Responses.txt', 'a') as ine:
                ine.write(f'{fmt}\n')
            with open('Database.txt', 'r+') as f:
                f.readline()
                data = f.read()
                f.seek(0)
                f.write(data)
                f.truncate()
                with open("Database.txt") as fp:
                    for i, line in enumerate(fp):
                        if i == 6:
                            lines = fp.readlines()
                            lines = lines[:-1]
                            break



async def wait_until_ready():
    await asyncio.sleep(10)
    print('works')


client.run(TOKEN)
