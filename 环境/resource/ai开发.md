powershell -c "irm bun.sh/install.ps1|iex"

git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup

npm install -g @fission-ai/openspec --allow-scripts=@fission-ai/openspec
openspec init
openspec update

/opsx-propose "创建一个后台管理程序，主要功能是定时采集数据，然后保存到数据库中，web界面上确认数据无误之后，点击发送或自动定时发送到云管服务器"
/opsx:apply
/opsx:sync 
/opsx:archive

openspec list
openspec view