# cover-rate
随机节点覆盖率
x=rand(1,100);
y=rand(100,1);
geshu=100;
r=0.2;
figure();
plot(x,y,'*');
figure();
plot(x,y,'*');
hold on
for i=1:100
    c(i,i)=1;
end
for i=1:1:100
		    for j=i+1:100
		        if sqrt((x(i)-x(j))^2+(y(i)-y(j))^2)<=r
		            c(i,j)=1;
		            c(j,i)=1;
                    plot([x(i);x(j)],[y(i);y(j)]);
                    hold on
                else 
                    c(i,j)=200;
                    c(j,i)=200;
		        end
		    end
end

for i=1:100
    c(i,i)=1;
end
for k=1:100
    for i=1:100
        for j=(i+1):100
            if(c(i,j)>c(i,k)+c(k,j))
                c(i,j)=c(i,k)+c(k,j);
                c(j,i)=c(i,k)+c(k,j);
            end
        end
    end
end
biaoji1=0;
for i=1:100
    for j=1:100
        if c(i,j)>102
            biaoji1=biaoji1+1;
        end
    end
end

if biaoji1==0
    disp('图连通')
else disp('图不连通')
end
figure();
rectangle('Position',[0,0,1,1],'facecolor','r','edgecolor','r'),axis equal;
axis([0,1,0,1]);
for i=1:100
rectangle('Position',[x(i)-r,y(i)-r,2*r,2*r],'Curvature',[1,1],'facecolor','g','edgecolor','g'),axis equal;
hold on;
axis([0,1,0,1]);
end
saveas(gcf,'fu4','jpg')
rgb=imread('fu4.jpg');
figure;
imshow(rgb);
R=rgb(:,:,1);  
G=rgb(:,:,2);  
B=rgb(:,:,3); 
[x2,y2,z2]=size(rgb); 
jishu2=0;
jishu3=0;
for i=1:x2  
    for j=1:y2  
        if((G(i,j)==0))  
            jishu3=jishu3+1;
        end  
    end  
end
for i=1:x2  
    for j=1:y2  
        if((R(i,j)==0))  
            jishu2=jishu2+1;
        end  
    end  
end
lv=jishu2/(jishu2+jishu3);
disp(lv)

