clear all
N=10000;
df1=80;
df2=20;
alpha_G=2.5;
alpha_g=2.5;
gamma_th_f=0.6;
rho_dB=40:3:80;
rho=10.^(rho_dB/10);
af=0.9;
an=0.1;
n1=5;
n2=10;
lambda1=1;
lambda2=2;
Y1=0;
Y2=0;
X1=sqrt(1/(2*lambda1))*randn(2*n1,N);
X2=sqrt(1/(2*lambda2))*randn(2*n2,N);
Y1=sum(X1.^2,1);
Y2=sum(X2.^2,1);
g1=sqrt(Y1);
g2=sqrt(Y1);
g3=sqrt(Y1);
g4=sqrt(Y1);
g5=sqrt(Y1);
g=[g1 g2 g3];
g_f=[g1 g2 g3 g4 g5];
G1=sqrt(Y2);
G2=sqrt(Y2);
G3=sqrt(Y2);
G4=sqrt(Y2);
G5=sqrt(Y2);
G=[G1 G2 G3];
G_f=[G1 G2 G3 G4 G5];
%G_theta_g=0;
G_theta_g=abs(G1).*abs(g1)+abs(G2).*abs(g2)+abs(G3).*abs(g3);
G_theta_g_f=abs(G1).*abs(g1)+abs(G2).*abs(g2)+abs(G3).*abs(g3)+abs(G4).*abs(g4)+abs(G5).*abs(g5);

 for  j=1:1:length(rho)
   count=0;
   for k=1:1:N
     gamma_df_xf=((df1^(-alpha_G)*df2^(-alpha_g)*af).*(G_theta_g.^2))./((df1^(-alpha_G)*df2^(-alpha_g)*an).*(G_theta_g.^2)+1./rho(j));
         if (gamma_df_xf(k)<gamma_th_f)
             count=count+1;
         end
   end
   Pout(j)=count/N;
 end
semilogy(rho_dB,Pout,'-*');hold on
for  j=1:1:length(rho)
   count=0;
   for k=1:1:N
     gamma_df_xf_f=((df1^(-alpha_G)*df2^(-alpha_g)*af).*(G_theta_g_f.^2))./((df1^(-alpha_G)*df2^(-alpha_g)*an).*(G_theta_g_f.^2)+1./rho(j));
         if (gamma_df_xf_f(k)<gamma_th_f)
             count=count+1;
         end
   end
   Pout_f(j)=count/N;
 end
semilogy(rho_dB,Pout_f,'-*');
legend('k=3','k=5');
xlabel('rho(dB)');
ylabel('Pout');
title('Pout Vs rho for far user'); 
