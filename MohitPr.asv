clc;
clear all;
close all;
%transmitter part
x1=input('Enter First Message Signal(4 bits): ');%first message signal
x2=input('Enter Second Message Signal(4 bits): ');%second message signal
x3=input('Enter Third Message Signal(4 bits): ');%third message signal
for j=1:400                                      %to spread the message signal
    if j>300
        m1(j)=x1(4);
        m2(j)=x2(4);
        m3(j)=x3(4);
    elseif j>200 && j<300
        m1(j)=x1(3);
        m2(j)=x2(3);
        m3(j)=x3(3);
        elseif j>100 && j<200
        m1(j)=x1(2);
        m2(j)=x2(2);
        m3(j)=x3(2);
    else
        m1(j)=x1(1);
        m2(j)=x2(1);
        m3(j)=x3(1);
    end            
end
figure(1);                                      %displays message signal
subplot(3,1,1)
plot(m1,'x');
title('First Message Signal');
subplot(3,1,2)
plot(m2,'x');
title('Second Message Signal');
subplot(3,1,3)
plot(m3,'x');
title('Third Message Signal');
ang1(1)=0;                                      %intial angle=0
ang2(1)=0;
ang3(1)=0;
z1(1)=0;
z2(1)=0;
z3(1)=0;
fc=0.05;                                            
t=0:0.01:100;
y=cos(2*pi*fc*t);                               %carrier wave
for i=1:4
    if x1(i)==1
        if ang1(i)==pi                         %increments angle by pi/2 if 1 is detected
            ang1(i+1)=-pi;
            z1(i)=1;
        else
            ang1(i+1)=ang1(i)+(pi/2);
            z1(i)=1;
        end
        
    else
          if ang1(i)==-pi                      %decrements angle by pi/2 if 0 is detected
            ang1(i+1)=pi;
            z1(i)=0;
        else
            ang1(i+1)=ang1(i)-(pi/2);
            z1(i)=0;
        end
       
    end
end
for i=1:4
    if x2(i)==1
        if ang2(i)==pi                         %increments angle by pi/2 if 1 is detected
            ang2(i+1)=-pi;
            z2(i)=1;
        else
            ang2(i+1)=ang2(i)+(pi/2);
            z2(i)=1;
        end
        
    else
          if ang2(i)==-pi                      %decrements angle by pi/2 if 0 is detected
            ang2(i+1)=pi;
            z2(i)=0;
          else
            ang2(i+1)=ang2(i)-(pi/2);
            z2(i)=0;
        end
       
    end
end
for i=1:4
    if x3(i)==1
        if ang3(i)==pi                         %increments angle by pi/2 if 1 is detected
            ang3(i+1)=-pi;
            z3(i)=1;
        else
            ang3(i+1)=ang3(i)+(pi/2);
            z3(i)=1;
        end
        
    else
          if ang3(i)==-pi                      %decrements angle by pi/2 if 0 is detected
            ang3(i+1)=pi;
            z3(i)=0;
        else
            ang3(i+1)=ang3(i)-(pi/2);
            z3(i)=0;
        end
       
    end
end
figure(2);                                     %to plot phase trillis diagram
subplot(3,1,1)
plot(ang1);
title('First Signal-PHASE');
subplot(3,1,2)
plot(ang2);
title('Second Signal-PHASE');
subplot(3,1,3)
plot(ang3);
title('Third Signal-PHASE');
for j=1:400
    if j>300
        mod1(j)=cos((2*pi*fc*j)+ang1(5));
    elseif j>200 && j<300
        mod1(j)=cos((2*pi*fc*j)+ang1(4));
        elseif j>100 && j<200
        mod1(j)=cos((2*pi*fc*j)+ang1(3));
    else
       mod1(j)=cos((2*pi*fc*j)+ang1(2));
    end            
end
for j=1:400
    if j>300
        mod2(j)=cos((2*pi*fc*j)+ang2(5));
    elseif j>200 && j<300
        mod2(j)=cos((2*pi*fc*j)+ang2(4));
        elseif j>100 && j<200
        mod2(j)=cos((2*pi*fc*j)+ang2(3));
    else
       mod2(j)=cos((2*pi*fc*j)+ang2(2));
    end            
end
for j=1:400
    if j>300
        mod3(j)=cos((2*pi*fc*j)+ang3(5));
    elseif j>200 && j<300
        mod3(j)=cos((2*pi*fc*j)+ang3(4));
        elseif j>100 && j<200
        mod3(j)=cos((2*pi*fc*j)+ang3(3));
    else
       mod3(j)=cos((2*pi*fc*j)+ang3(2));
    end            
end
figure(3);                                  %to plot the modulated signals(cpm)
subplot(4,1,1)
plot(t,y);
title('Carrier Wave');
subplot(4,1,2)
plot(mod1);
title('First CPM modulated Signal');
subplot(4,1,3)
plot(mod2);
title('Second CPM modulated Signal');
subplot(4,1,4)
plot(mod3);
title('Third CPM modulated Signal');
for i=1:1200
    if i>800
        tr(i)=mod3(i-800);
    elseif i<=800 && i>400
        tr(i)=mod2(i-400);
    else
        tr(i)=mod1(i);
    end
end
figure(4);                                %to plot the transmitted signal(fdm)
plot(tr);
title('Transmitted FDM wave');
%reciever part
for i=1:400
    re1(i)=tr(i);
    re2(i)=tr(i+400);
    re3(i)=tr(i+800);
end
figure(5);                                 %to plot after fdma
subplot(3,1,1)
plot(re1);
title('First Signal After FDMA');
subplot(3,1,2)
plot(re2);
title('Second Signal After FDMA');
subplot(3,1,3)
plot(re3);
title('Third Signal After FDMA');
for i=1:400
    if re1(i)==cos((2*pi*fc*i)+ang1(2))
        ou1(i)=z1(1);
    elseif re1(i)==cos((2*pi*fc*i)+ang1(3))
        ou1(i)=z1(2);
    elseif re1(i)==cos((2*pi*fc*i)+ang1(4))
        ou1(i)=z1(3);
    elseif re1(i)==cos((2*pi*fc*i)+ang1(5))
        ou1(i)=z1(4);
    end
end
for i=1:400
    if re2(i)==cos((2*pi*fc*i)+ang2(2))
        ou2(i)=z2(1);
    elseif re2(i)==cos((2*pi*fc*i)+ang2(3))
        ou2(i)=z2(2);
    elseif re2(i)==cos((2*pi*fc*i)+ang2(4))
        ou2(i)=z2(3);
    elseif re2(i)==cos((2*pi*fc*i)+ang2(5))
        ou2(i)=z2(4);
    end
end
for i=1:400
    if re3(i)==cos((2*pi*fc*i)+ang3(2))
        ou3(i)=z3(1);
    elseif re3(i)==cos((2*pi*fc*i)+ang3(3))
        ou3(i)=z3(2);
    elseif re3(i)==cos((2*pi*fc*i)+ang3(4))
        ou3(i)=z3(3);
    elseif re3(i)==cos((2*pi*fc*i)+ang3(5))
        ou3(i)=z3(4);
    end
end

figure(6);                              %detected signal
 subplot(3,1,1)
 plot(ou1,'x');
 title('First Detected Signal');
 subplot(3,1,2)
 plot(ou2,'x');
 title('Second Detected Signal');
 subplot(3,1,3)
 plot(ou3,'x');
 title('Third Detected Signal');