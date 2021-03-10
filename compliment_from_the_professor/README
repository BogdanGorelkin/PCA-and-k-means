```Matlab
clear all;
close all;
clc;
load matricecentresmailles.txt;
matrice=matricecentresmailles;
Lmat=length(matrice);

%% we starting from 2 because we don't interesting for k=1 and k=2
for K=2:24
[idxK,cent,sumdist] = kmeans(matrice,K,'start','sample','emptyaction','drop','dist','sqEuclidean','display','off','replicates',100);
[silhCI] = silhouette(matrice,idxK,'sqEuclidean');
meanCI=mean(silhCI);
names=num2str(idxK); %noms des clusters
k(K)= K;
z(K)=meanCI;
end
z(1) = NaN;
z(2) = NaN;

figure('Name','K of MeanCI','NumberTitle','off');
plot(k, z)

%% For k = 7 we have maximum meanCI so let's use this value
K=7;%number of clusters

[idxK,cent,sumdist] = kmeans(matrice,K,'start','sample','emptyaction','drop','dist','sqEuclidean','display','off','replicates',100);
%[idxK,cent,sumdist] = kmeans(matrice,K,'start','sample','emptyaction','drop','dist','cityblock','display','off','replicates',100);
%dlmwrite('clusteringEn3clusters.txt',idxK,'delimiter', '\t');
%dlmwrite('clusteringEn3clusters.txt',idxK,'delimiter', '\t');

figure('Name','Clastering','NumberTitle','off');
[silhCI] = silhouette(matrice,idxK,'sqEuclidean');
silhouette(matrice,idxK,'sqEuclidean');
meanCI=mean(silhCI);
names=num2str(idxK); %noms des clusters
TB=rand(K,3); % color chart
figure;%('Name','Clastering','NumberTitle','off');
% cla(ma_zone_graphique); % will allow you to erase when you need it
axis equal;
hold on; 
grid on;
plot(-39417.868029015925, 167937.51495581277,'s','LineWidth',2,'MarkerSize',15, 'MarkerEdgeColor','r','MarkerFaceColor',[1,0,0]);
text(-39417.868029015925+0.09, 167937.51495581277+0.09,{'Origine'});
plot(-46079.837095297975, 165848.46951636527,'s','LineWidth',2,'MarkerSize',15, 'MarkerEdgeColor','r','MarkerFaceColor',[1,0,0]);
text(-46079.837095297975+0.09, 165848.46951636527+0.09,{'Destination'});


xcote=300;
ycote=300;
Vectmailles=matrice(:,3);
valMaxMaille = max(Vectmailles);
for i=1:Lmat
    x=matrice(i,1)-150;
    y=matrice(i,2)-150;
couleur = TB(idxK(i),:);
transparence=((0.95*matrice(i,3))/valMaxMaille);
draw_square(x,y,xcote,ycote,couleur,transparence);
end

plot(matrice(:,1),matrice(:,2),'.');%trace the centers of the Meshes
text(matrice(:,1)+0.01,matrice(:,2)+0.01,names);%trace the names of the Meshes
plot(cent(:,1),cent(:,2),'s','MarkerFaceColor',[1,0,0]); % trace the mesh centers
text(cent(:,1),cent(:,2),' \leftarrow C','Color','r'); % trace the text center of the meshes

%hold off

```
