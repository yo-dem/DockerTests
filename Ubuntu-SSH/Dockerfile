# Crea un immagine a partire dall'imagine padre ubuntu
FROM ubuntu

# Aggiorna l'istanza creata
RUN apt update && apt upgrade -y

# Installa SSH server
RUN apt install openssh-server -y

# Configura la password e il nome utente per ssh
RUN echo 'root:password' | chpasswd
# Sostituisce tramite sed la riga che permette di abilitare la password su ssh
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config

# Avvia il servizio ssh
RUN service ssh start

# Espone la porta 22 nel container
EXPOSE 22

# Avvia il servizio come demone
CMD ["/usr/sbin/sshd","-D"]


