# Powershell-Script
PowerShell ile Birden Fazla Sunucuda Kullanıcı Ekleme İşlemleri

#Sunucu listesini belirtiniz.
$servers = @("SRV-01", "SRV-02", "SRV-03")

#Eklemek istediğiniz kullanıcı adlarını belirtiniz.
$usersToAdd = @("user1@kayasystem.com", "user2@kayasystem.com", "user3@kayasystem.com")

#Her sunucu için işlem yapılır.
foreach ($server in $servers) {
    Write-Host "Sunucu: $server"
    
    #Sunucuya oturum açılır.
    $session = New-PSSession -ComputerName $server
    
    #Her kullanıcı için işlem yapılır.
    foreach ($user in $usersToAdd) {
        #Kullanıcıyı Administrator grubuna ekle
        Invoke-Command -Session $session -ScriptBlock {
            Add-LocalGroupMember -Group "Administrators" -Member $using:user
        }
        
        Write-Host "$user, $server sunucusunun Administrator grubuna eklendi."
    }
    
    #Oturumu kapat
    Remove-PSSession -Session $session
}
