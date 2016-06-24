clear all; 
imagefiles = dir('*.jpg');
avgpoints=[];
write_dir='../';
    for i = 1:length(imagefiles)
        filename = [imagefiles(i).name];
        fprintf('Working on %s \n',filename);
        image= imread(filename); 
        [~,name,~]=fileparts(filename);
        points=load(strcat(name,'.txt'));
        points=[points; 1 1; size(image,2)/2 1; size(image,2) 1; size(image,2)... 
            size(image,1)/2;size(image,2) size(image,1); size(image,2)/2 size(image,1);... 
            1 size(image,2)];
        f=fopen(strcat(write_dir,filename,'.txt'),'wt');
        fprintf(f,'%d %d\n',int8(points'));
        fclose(f);
        avgpoints=[avgpoints points];
    
    end
avgpoints=[(avgpoints(:,1)+avgpoints(:,3))/2 (avgpoints(:,2)+avgpoints(:,4))/2];
tri=delaunay(avgpoints(:,1),avgpoints(:,2));

file=fopen(strcat(write_dir,'tri.txt'),'wt');
fprintf(file,'%d %d %d \n',int8(tri'));
fclose(file);