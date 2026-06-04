Hey everybody, I'm Jamie. Welcome back to 
Teachers Tech. So, in my last Claude Code video,  
we did something pretty cool. We built a full 
bookmark dashboard app just by typing in plain  
English. No coding experience needed. If you 
haven't seen that one, I'll link it right up  
here and down below in the description. Definitely 
go watch that one first because today's video  
builds on everything we covered there. But today, 
we're going to go way beyond building apps. Today,  
we're going to be building an AI agent. Let 
me show you what I mean. Are you seeing this?  
I typed one sentence and it started thinking on 
its own. It broke the task into steps. It asked  
me follow-up questions. It went out to gather 
information, organized everything, and produced  
a full report all by itself. Last time, Cloud 
Code did what we told it to do. This time, we're  
going to teach it to figure out things on its own. 
That's called an agentic workflow, and honestly,  
it's the most useful thing I've learned in AI this 
year. Oh, and we're doing the whole thing inside  
VS Code this time. way more comfortable than 
the raw terminal like last time. Let's get into  
it. All right, before we start building anything, 
let's talk about what an agentic workflow actually  
is because it sounds way more complicated than it 
really is. Think back to the last video. We told  
Claude Code exactly what to build. We said, "Make 
me a bookmark dashboard with search dark mode."  
We gave it specific instructions and it followed 
them. That was powerful, but we're still doing  
all the thinking. We were directing every step. 
An agentic workflow flips that around. Let me  
break it down into three levels so you can see the 
differences. Level one is chat. This is the most  
basic way people use AI. You ask a question, you 
get an answer. One and done. That's your standard  
chat GPT or clawed conversation. Most people never 
get past this level. Level two is building. This  
is what we did in the last video. You tell 
the AI what you want to create. You guide the  
process step by step and it writes the code for 
you. You're the director, the AI is the builder.  
It's way more powerful than just chatting, but 
you're still making all the decisions. Level three  
is agentic. And this is where things get really 
interesting. Instead of telling the AI what to  
do step by step, you describe the goal. You say, 
"Here's what I need to accomplish." And the AI  
figures out the steps on its own. It makes a plan, 
picks its tools, adapts when things don't go as  
expected, and it will even ask you questions when 
it's not sure about something. That's what we're  
doing today. Here's the way I think about it. It's 
like the difference between micromanaging a brand  
new employee versus trusting an experienced one. 
In the last video, we were the manager saying,  
"Do this, then this, then this." Today, 
we're saying, "Here's the goal. Here's  
what you have access to. Figure it out." That's a 
completely different relationship with the AI. So  
what specifically makes something agentic? Three 
things. First, it follows a process. It's not just  
answering a single question. It's working through 
a whole series of steps to get a result. Second,  
it makes decisions. It chooses what to do based 
on what it finds along the way. If one approach  
isn't working, it pivots. If it finds something 
unexpected, it adjusts. Third, it asks before it  
assumes. Instead of guessing what you want, a good 
aenic workflow will ask you clarifying questions  
first. That one change alone makes the output 
10 times better. And the use cases for this are  
endless. You could use it to research a topic 
across multiple sources and compile a report.  
Analyze a folder of files and organize them by 
category. Draft personalize emails for a whole  
list of contacts. Compare competitors and produce 
a sidebyside breakdown. The pattern is always  
the same. You give it the goal and it does the 
work. All right, let's get our tool set up. Now,  
last time we worked entirely in the terminal and 
that works, but VS Code gives us a much better  
experience for what we're going to do today. You 
can see your files, your code, and cloud code all  
in the same place. When the agent is creating and 
editing multiple files, which it will be, having  
that visual file explorer makes a huge difference. 
So, let's get this set up. This only takes about  
2 minutes. If you don't have Visual Studio Code 
on your computer, I'll put the link to this site  
down below in the description. Then you can pick 
what operating system you're working on. Today I'm  
going to be on Windows, so I'm going to go ahead 
and choose this and download this for my machine.  
Once you have it downloaded, go ahead open it up. 
Where I want you to go is right here to extensions  
and you're going to type in just claude code 
up here. And you're going to see that we can  
install cloud code here. So I'm just going to go 
ahead and click on this. I'm going to trust the  
publisher and this install. All right, it's all 
ready to go. We have it installed. I can see the  
cloud code. I'm going to click on it to open. I'm 
going to go and mark this as done. I'm just going  
to go and close these extensions over here. I'll 
just click on it again to give myself more room.  
Notice you can uh stretch these uh to whatever 
you want that works best for your preferences.  
If you already installed Cloud Code from the 
last video, you're all set. The extension uses  
the same installation. If you haven't installed it 
yet, go watch that first video because we covered  
the whole setup there. Let me give you a quick 
orientation of VS Code. Over here on the left,  
we've got our file explorer. This is where you're 
going to see every file the agent creates in real  
time. Folders appearing, documents being written. 
It's really satisfying to watch. Over here, we  
have our cloud code panel. This is where you talk 
to the agent. You go down here, type your prompts,  
you see what it's thinking, and you watch it work. 
Now, let's create our project folder. I'm going to  
go ahead and create a new folder where we're going 
to be working out of. I'm just going to click open  
folder. And I haven't created one yet. If you know 
what folder you want, you can go ahead and choose  
that one. I'm going to go in my documents here. 
And I'm just going to create a brand new folder.  
And I'm going to go call it my first agent. 
Select folder. I'm just going to go back and  
click on clawed code here and new session just to 
open that back up. And if I click on the explorer,  
you can see here's the folder that I just created. 
Now, there's a couple of features in VS Code that  
are going to be really important for you today. 
First, you can see the files updating real time as  
the agent works. Watch the file explorer. When the 
agent creates something, it just appears. Second,  
when the agent plans a multi-step task, you'll 
see a to-do list pop up showing you exactly  
what's going to do and where in the process. 
And here's the big one, planning mode. Press  
shift plus tab and you'll toggle into planning 
mode. In this mode, Claude Code thinks and plans  
but doesn't actually change any files. It's like 
a dry run. We're going to use this a lot today  
because the key to aenic workflows is planning 
before building. All right, our environment is  
ready. Now, let's set up one more thing that's 
really going to make all the difference. Okay,  
this is something I didn't cover in the first 
video and it completely changes how claude code  
works for you. It's a file called claude.md. 
And I'm not exaggerating when I say this is  
the single most important thing you can set up. 
So, what is claw.md? It's a simple markdown file  
that you put in your project folder. Claude code 
reads it automatically every time it starts up.  
Think of it like an onboarding document for a 
new employee. It tells the agent who you are,  
what the project's about, and how you want things 
done. Let's build one together right now. In VS  
Code, I'm creating a new file in the root of our 
project. I'll name it claude.md all caps. And now,  
let's fill it in section by section. Okay, the 
first section is going to be project context. And  
this is going to tell the agent what the workspace 
is for. So I am going to give it a heading right  
here at the beginning. And to do this, use the 
pound key and then a space. And then you can just  
type your heading. You'll notice how it turns 
blue. I'm just going to give it a couple spaces  
just so everything's easier to read and so I can 
take a quick glance at and see what's happening.  
I'm going to go and put this. So for project 
context, this is my AI agent workspace. I use it  
for research, content creation, and productivity 
workflows. I'm going to give it a couple spaces.  
Next is the about me. This is where you tell the 
agent about who you are, what what you care about.  
So, I'll give it again another header and give 
it a couple spaces. And this is what I'm going  
to put. I create content about technology and 
productivity. My audience is people who want  
practical, nononsense tutorials. I prefer clear, 
jargon-free output. Now, the most important part,  
rules. This is where you set the guardrails. These 
are the instructions the agent will follow every  
single time. Let's give it a heading and a couple 
spaces. And my rules are going to be listed with  
dashes in front of them. So you can have a clear 
list just like this. So always ask clarifying  
questions before starting a complex task. Show 
your plans and steps before executing. Keep  
reports and summaries concise, bullet points over 
paragraphs. Save all output files to the output  
folder and site sources when doing research. And 
finally, project structure. This tells the agent  
where things go. And this is where I want things. 
I have my workflows. Workflow instruction files.  
My output are the finished deliverables. And 
resources are the reference docs and templates.  
I'm just going to save this now by hitting ctrls 
together. That took us about 2 minutes. But now,  
every single time you open Claude Code in this 
folder, it already knows your preferences, your  
rules, and exactly how you want things organized. 
No repeating yourself. Let me show you why this  
matters so much. Now, I'm going to use the same 
prompt, research remote work trends on the left  
without claw.md. I made a separate folder with no 
claw.md file in it. So, I get this generic wall  
of text. You can see as it goes through, there's 
not really much structure. I get one question just  
about allowing something uh just kind of a data 
dump. But on the right with the claw.md file,  
the agent's asking me many different questions 
as it goes through it. Then it gives me organized  
bullet list, clear sections, source cited, and 
save the file exactly where I told it to. Let's  
take a look at this end file here. Here's the link 
to the report, and it's in the output. Remember,  
I told it to uh go ahead and put it the finished 
output in here. So, if I click on it, it brings  
me to this. Now, you might be thinking, well, that 
doesn't look very good. But there's a shortcut to  
see what it looks like. So, if you go to control, 
shift, and v uh together, when you click in here,  
if you press all those keys together, you get 
the report, what it created for you. So, as I  
go through it, you can see how much more detailed 
uh this was. Here we have our key takeaways. we  
have all of this information versus that that one 
little short link that we had with the uh without  
the claw.md file. And this is why the claw.md is 
non-negotiable. 2 minutes of setup saves you hours  
of frustration down the road. And here's something 
that was just added to claude code that makes this  
even more powerful. Automatic memory. As the agent 
works through your project, it now automatically  
records things it learns and recalls them in the 
future sessions. So, it's just not reading your  
claw.md at startup anymore. It's also building its 
own understanding of your project over time. The  
more you use it in this folder, the smarter it 
gets about your preferences and how things are  
organized. Before we start building our agent, 
I want to give you the mental model. There are  
three pieces that make agendic workflows work. And 
once you understand them, everything else clicks  
into place. Layer one, workflows. These are just 
plain English files that describe a process step  
by step. Think of them like a recipe. The agent 
reads the recipe and follows it, but it's smart  
enough to adapt if anything's off. Workflows live 
as a simple markdown file in your project. Nothing  
fancy. Layer two, the agent. This is just 
cloud code itself. It reads your workflows,  
thinks through the steps, and makes decisions. You 
don't program the agent. You don't write the code  
for it. You just give it clear instructions and 
let it reason. Layer three tools. These are what  
the agent uses to actually get things done. Out 
of the box, Claude Code can read and write files,  
run terminal commands, and search the web. That's 
right. Web search is built right in. No extra  
setup needed. The agent can go out, find current 
information, and bring it back into your project.  
Now, you can also connect external services like 
Gmail, Notion, and databases using something  
called MCP. That's model context protocol. That 
opens up a whole world of possibilities, and we'll  
cover that in depth in the next video. But for 
today, the built-in tools are more than enough for  
everything we're doing. And here's the key insight 
that most people miss. Most people skip straight  
to the fancy tools and plugins. But the real power 
is writing good workflows. A well-written workflow  
with basic tools will outperform a sloppy 
prompt with every plug-in in the world. The  
workflow is where the magic lives. Okay, enough 
theory. Let's build our first agent. All right,  
I'm in our empty project. You can see I just have 
the claw.md file that we created. I deleted those  
other test folders when I ran through that quick 
test. The uh first thing we're going to do is go  
and change it to plan mode. So, when I'm inside 
the chat down here, I'm just going to press shift  
and tab. But notice if I press it once, it goes 
to edit automatically. I need to press it one  
more time, it brings me to plan mode. If I press 
it again, it brings me back to where I was. So,  
two times pressing shift and tap brings me over 
to plan mode. Now, plan mode means Cloud Code will  
think and plan, but won't change any files. We're 
going to design our workflow before building it.  
Always plan first. Now, I'm going to describe what 
I want. And watch carefully. I'm not giving it  
step-by-step instructions. I'm describing my goal. 
And this is what I'm going to say. I want to build  
a workflow where I can give you a topic. You'll 
research it thoroughly, organize the findings,  
and produce a clean, structured report. Before you 
start researching, you should ask me clarifying  
questions about the scope, the audience, and what 
I specifically want to know. I'm going to submit.  
Look at this. I gave it a goal and it's already 
breaking it down into steps. It's thinking about  
what the workflow needs. A clarifying question 
phase, a research phase, a synthesis phase,  
an output phase. It's even suggesting quality 
checks. That's the agendic thinking and action.  
I didn't tell it these steps. It figured them out. 
But I want to add one more thing before we build.  
Before I add one more thing, let's go ahead and 
take a look what it has already. Here we have a  
resource plan workflow. And if I scroll through, 
I can see there's some files that are going to be  
created. And remember once we accept it to keep an 
eye over on explore here because you're going to  
see it get created. It's going to uh go ahead 
and create this research report uh.md as I go  
down. Step two, confirm the plan. Three, research. 
Four, write the report. Five, save the output. It  
gave me some formatting. So, if I like everything 
here, I could go ahead yes and auto accept or yes,  
manually approve or keep planning. But what I'm 
going to say is this. I also want the report to  
include a section at the end with key takeaways 
and recommendations for the next step. So,  
I'm just going to put that in and hit enter. So, 
it's going to update the plan. It doesn't just  
start over. It just folds the new requirement into 
what it already had. So, that's why plan mode is  
so valuable. you can shape the approach before 
anything gets built. So I can see now it says  
uh right here plan updated the report template 
will now include two additional sections here I  
have recommended next steps key takeaways. So I'm 
going to go ahead and you know what I'm going to  
I'm happy with it. Let's build it and I'm going 
to go to auto accept. So it's just going to go  
through and accept everything. So you're going 
to see the mode change from plan and as I click  
on this just keep an eye on explorer. So notice 
we have our workflows. If I go ahead and open it,  
it's still working, but we have the research 
report MD that I said it was going to create.  
Now let's look at what it actually wrote. This is 
the important part. So I'm I'm going to go to the  
research report MD file and just double click 
on it. And you'll see it opens up. We have the  
uh chat over here with it. But here we have the 
file. Now, at the top, I've got its objective  
or purpose here. A clear statement of what the 
workflow does. Given a topic from the user, ask  
clarifying questions. Conduct structured research. 
Okay. So, let's move down to the next. We have the  
qualifying question steps. Ask the user these 
questions. And you get an idea. What are the  
specific angles of the questions you want covered? 
Who will read the report? Do you want a quick uh  
overview or deep dive? And you can see the other 
ones that include uh format preferences. Now,  
this is what makes it a gentic rather than just 
a dumb text generator. It's going to check with  
you before it runs off and does the work. So, 
no more garbage output because it guessed wrong  
about what you wanted. So, then it moves down. 
We can see it confirmed the plan after receiving  
the answers. Confirm the research plan with users 
before starting. We have step three, the research  
topic. as we uh go through and look at the details 
for each of these, you know, like avoid opinion  
only posts. Uh for recent developments, include 
sources from the last 12 months where possible  
uh what to look for while researching. Now we're 
on to writing the report with the writing rules,  
the tone, and then saving the output. And we do 
have some error handling. If the topic is too  
broad to research meaningfully, say so and ask the 
user to narrow it. Now, here's the be beautiful  
part about all this. Every single word in this 
file is just plain English. There's no code,  
no special syntax. If you wanted to change 
something like adding a step where it creates a  
summary table or removing the clarifying questions 
for quick task, you just edit the text. The agent  
adapts to whatever you write. So, that's the 
power of this approach. I want to go back over  
to Claude Code and ask this question right here. 
What workflows do you have available? And look,  
it lists our research report workflow and 
describes exactly what it does. It knows what  
it's capable of now. So, let's put this to work. 
Now, for the fun part, I'm going to give it a real  
research task and we're going to watch the whole 
agentic workflow run from start to finish. I'm  
going to go and put this in. I want to research 
the current state of AI agents in 2026. What are  
people actually using them for? What's working? 
What's overhyped? And where things are heading.  
Now, watch. The first thing it should do is ask 
me questions because that's what the workflow  
says to do. So there it is. Look, it's asking, 
you know, the audience, the scope, the depth,  
all these questions. Now, I need to answer it, 
but I can answer it naturally, like I'm talking  
to a colleague, and this is how I'm going to do 
it. Keep it broad. I want a hype versus reality  
breakdown. The audience is techsavvy people 
who are curious about AI, but not necessarily  
developers. Medium depth. include specific tools, 
platforms, stick to the last 6 to 12 months, and  
formatted structured posts for clear sections and 
bulleted points. So, let's submit. Now, it's going  
to take those answers and start working. Watch the 
to-do list. Now, here's the plan before it starts.  
You can see AI agents 2026, what people are 
actually doing, all the uh things I just answered,  
what questions I'll research are these ones, 
and I'm just going to say proceed. Yes. And  
notice now even on the side we have resources a 
folder that's there. I'm going to say allow. Yes.
So it's searching the web, reading through 
results, pulling out relevant information.  
You can see it thinking through what it finds. 
And remember this is web search built right into  
cloud code. No plugins, no MCP setup, no 
BI API keys. It just works out of the box.  
Now I have to allow it to write. All right, 
it's all done. The link to the finished report  
is here. It's also in my output. It lives right 
here. It's the same thing. Now, the one thing I  
just wanted to point out here, this right here, 
the uh most honest number, even the best models  
only succeed 45.7% of the time on real world task. 
Human oversight isn't optional yet. I wonder how  
fast this number will change. I must say it's kind 
of comforting to know this. But let's go ahead and  
open up the report. So remember when it opens 
up the MD file, this is in markdown uh language  
here. So it doesn't look quite as nice as the 
formatted report. But if we hit control, shift,  
and v together, it's going to give the preview of 
it. So we have the topic and everything that we  
said said wanted in it from the depth of 3 to five 
pages, the date range, the audience. We have our  
executive summary up top here, background, 
uh what are the what's actually working,  
key findings. So, we have this detailed report now 
going all the way through uh really narrowing down  
specifically what I told it to search. So, 
each time I do this, it's going to be very  
specific. It gives me all the sources to this. 
So, the agent did all the thinking, organizing,  
and all the writing. But we're not done yet. Let 
me show you one more thing that makes the agendic  
workflow so powerful. Iteration. I'm going to 
say this. The executive summary is a bit long.  
Trim it to three bullet points. Now watch. It 
doesn't start over again. It goes into the report,  
finds the executive summary, and trims it down. 
Clean, targeted, edited. And one more thing I  
wanted to do, add a comparison table of the top 
five AI agent tools mentioned in the report.  
So, look at that. It scans through what it already 
wrote, identifies the tools it mentioned, and  
created a formatted comparison table. It didn't 
need me to list the tools. It pulled it from its  
own research. Let's go check out those changes. 
So, I'm just going to open back up this. I'll go  
back to preview. We should see a shorter summary. 
There's the three. 1 2 3. And now, uh, before this  
was six. It didn't have quite the comparison 
on it, but now 1 2 3 4 five on it. So, it made  
those quick updates to the files. That's what I 
mean by Agent. It remembers the context and it  
knows the project and it builds on what's already 
there instead of starting from scratch each time.  
Once you start working this way, it's really hard 
to go back. All right, before we wrap up, let me  
save you some time with the five biggest mistakes 
I see people make and some pro tips that go with  
them. Mistake number one, skipping claw.md. I 
know I keep saying it, but this one file changes  
everything. Two minutes of setup saves you hours 
of frustration. Just do it. Mistake number two,  
being too vague. Do some research gives you 
generic garbage, but research remote working  
trends for general audience. Focus on productivity 
data from the last 6 months and formatted as a  
structured report with bullet points. That gives 
you gold. Being specific is everything. Mistake  
number three, not using plan mode. If you skip 
planning and jump right to execution, the agent  
might go down the wrong path and you've wasted 
your time. Plan first, build second. It takes an  
extra 30 seconds, but it's well worth it. Mistake 
number four, not telling it to ask questions.  
If your workflow doesn't say ask clarifying 
questions before starting, the agent will assume,  
and assumptions lead to wasted time and mediocre 
output. Always build that check-in step. Mistake  
number five, trying to build everything at once. 
Start with one workflow, get it working well,  
refine it, then build the next one. Don't try to 
automate your entire life in a single weekend.  
Trust me on this one. Now, here are some quick 
pro tips. Keep your workflow files in a workflow  
folder. It keeps things organized as you build 
more of them. Read the agents to-do list and  
reasoning as it works. It's the best tool you have 
for understanding what's happening and catching  
mistakes early before they snowball. When the 
output isn't right, tell the agent specifically  
what to fix. Don't start over. Targeted feedback 
is way faster than redoing the whole thing. And  
save your best claw.md and workflow files. You can 
copy them into new projects as starting points.  
Over time, you'll build a library of workflows 
that make it incredibly efficient. One more,  
and this is a really useful one. If the 
agent goes off in the wrong direction,  
hover over a previous point in the thread, and 
you have the option to roll back the conversation,  
and this undoes file changes that the agent made. 
So, you can rephrase your prompt and try again. No  
need to manually undo edits or start over again. 
It's a great safety net, especially when you're  
still learning how to write good prompts. And 
finally, effort levels. Type effort followed by  
low, medium, or high to control how deeply 
the agent thinks before responding. Low is  
fast and lightweight, great for simple edits. High 
means it really slows down reasons carefully and  
produces its best work. Use that for more complex 
research or multi-step task. If you're not sure,  
just leave it on the default and Claude will 
figure it out. But knowing this dial exists is  
useful once you start running longer workflows. 
Let's bring it all together. In the first video,  
we used Claude code to build an app. Today, we 
used it to build an agent. The first one does  
what you tell it. The second one figures things 
out on its own. That's a huge jump. And that's  
what you did today. So, here's my challenge 
for you. Build one workflow this week, just  
one. Pick something you do regularly, research, 
writing, organizing, analysis, whatever it is,  
and turn it into a workflow file. It doesn't have 
to be perfect. Just get it running and see what  
happens. Let me know down below in the comments 
what you come up with. I'm always curious to see  
what people are thinking about, what they could 
automate through one of these workflows. Thanks  
for watching this time on Teachers Tech. I'll see 
you next week with more tech tips and tutorials.