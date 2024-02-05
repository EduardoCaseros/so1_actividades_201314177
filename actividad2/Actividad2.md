## Crear un archivo bash con el siguiente código 
#!/bin/bash

echo "Por favor, ingresa tu nombre de usuario de GitHub:"
read GITHUB_USER

API_URL="https://api.github.com/users/$GITHUB_USER"

response=$(curl -s $API_URL)

user_id=$(echo $response | grep -o '"id":[^,}]*' | cut -d':' -f2)
created_at=$(echo $response | grep -o '"created_at":[^,}]*' | cut -d':' -f2)


system_date=$(date +"%Y%m%d_%H%M%S")


log_file="/tmp/$system_date/saludos.log"

echo "Hola $GITHUB_USER. User Id: $user_id. Cuenta creada el: $created_at" > "$log_file"




## Crear el cron Job 
1. crontab -e
2. */5 * * * * /script.sh

