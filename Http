local audio_manager = {}
local MediaPlayer = luajava.bindClass("android.media.MediaPlayer")
local File = luajava.bindClass("java.io.File")
local projectPath = tostring(activity.getLuaDir())

function audio_manager.playEffect(fileName, volume)
    local path = projectPath .. "/Audios/" .. fileName
    local file = File(path)
    if file.exists() then
        local mp = MediaPlayer()
        mp.setDataSource(path)
        mp.prepare()
        local vol = volume or 1.0
        mp.setVolume(vol, vol)
        mp.start()
        mp.setOnCompletionListener(function(m) m.release() 
end)
    else
        print("Audio file missing: " .. fileName)
    end
end

function audio_manager.playRandomEffect(fileList, volume)
if #fileList > 0 then
math.randomseed(os.time())
local randomIndex = math.random(1, #fileList)
local selectedFile = fileList[randomIndex]
audio_manager.playEffect(selectedFile, volume)
end
end
return audio_manager
