-- Iruc

loluser=game:service'Players'.localPlayer;
lolmouse=loluser:getMouse();
lolchar=loluser.Character;

-- got stupid didnt feel right over here 

keys={r=true;};
tele={t=true;};
objc={v=true;};

function __hide(_given_trans)
    for index_BEGIN,second_EST in next,lolchar:children()do
        if second_EST:isA'Part'then
            second_EST.Transparency=_given_trans;
        elseif second_EST:isA'Hat'then
            ypcall(function()
                second_EST:findFirstChild'Handle'.Transparency=_given_trans;
		game.Workspace.Iruc.Head.face:Remove()
            end);
        end;
    end;
end;

lolmouse.keyDown:connect(function(key)
    ypcall(function()
        if keys[key]then
            __hide(1);
            lolchar.Humanoid.WalkSpeed=100;
        elseif tele[key]then
            lolchar:moveTo(lolmouse.hit.p);
        elseif objc[key]then
            game:service'Lighting'.TimeOfDay=0;
        end;
    end);
end);

lolmouse.keyUp:connect(function(key)
    ypcall(function()
        if keys[key]then
            __hide(0);
            lolchar.Humanoid.WalkSpeed=16;
            lolchar:findFirstChild'HumanoidRootPart'.Transparency=1;
        end;
    end);
end);

throwmsg=Instance.new'Message';
throwmsg.Parent=loluser.PlayerGui;
throwmsg.Text='Trekker Utl Loaded	Made by ("Iruc")';
wait(3)
game.Players.localPlayer.PlayerGui.Message:Remove()
