p=[0.5 0.25 0.125 0.125];
a(1)=0;
m=4;
for i=2:m
    a(i)=a(i-1)+p(i-1);
end
for i=1:m
    n(i)=ceil(-1*log2(p(i)));
end
for i=1:m
    z=[];
    int=a(i);
    for j=1:n(i)
        frac=2*int;
        c=floor(frac);
        frac=frac-c;
        z=[z,c];
        int=frac;
    end
    z
end
ent=0;
nl=0;
cl=0;
for i=1:m
ent=ent+p(i)*log2(1/p(i));
nl=nl+p(i)*n(i);
cl=cl+n(i);
end
efficiency=ent/nl*100
compressed_length=8*m/cl
