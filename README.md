# Create-Team
New Microsoft Team

$UserCredential = Get-Credential 
$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $Session

Connect-MicrosoftTeams

$group = New-Team -MailNickname "TestTeam" -displayname "Test Teams" -Visibility "private" -description "ISD Test PLC" -template "EDU_PLC"

Add-TeamUser -GroupId $group.GroupId -User "pattiw@eupschools.org"
Add-TeamUser -GroupId $group.GroupId -User "jmarra@eupschools.org"
#Add-TeamUser -GroupId $group.GroupId -User "wilma@example.com"
New-TeamChannel -GroupId $group.GroupId -DisplayName "Find Me"
New-TeamChannel -GroupId $group.GroupId -DisplayName "Help Desk"
#New-TeamChannel -GroupId $group.GroupId -DisplayName "Contracts"

Remove-PSSession $Session
