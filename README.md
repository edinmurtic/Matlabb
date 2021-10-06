# Matlabb
function[rez]=funk(t,p)

R=5;
L=10*1e-3;
C=100*1e-6;
E=100;

rez=zeros(2,1);
rez(1)=(1/L)*(-p(2)-3*p(1));
rez(2)=(1/C)*(p(1)-p(2)/R);

end

ode23(@funk, [0:0.0001:0.01], [10;50])
[t, p] = ode23(@funk, [0:0.0001:0.01], [10;50]);
figure
i = p(:,1);
plot(t, i) , title('Vremenske promjene struje kroz zavojnicu');
grid
xlabel('Vrijeme');
ylabel('Struja');

figure
u = p(:,2);
plot(t, u) , title('Vremenske promjene napona na kondenzatoru');
grid
xlabel('Vrijeme [s]');
ylabel('Napon [V]');
