# test_demo: PowerShell script to get all the site owners of all the SharePoint sites
foreach($site in $sites)
{
$siteURL = $site.Url
$siteOwner = $site.Owner

    Write-Host $siteURL -ForegroundColor Blue
Write-Host $siteOwner -ForegroundColor Blue

$siteAdmins = Get-SPOUser -Site $siteURL -Limit All | select LoginName,IsSiteAdmin | ? { $_.ISSiteAdmin }

$siteUsers = “”
foreach($siteAdmin in $siteAdmins) { $siteUsers += $siteAdmin.LoginName + ” , ” }
    Write-Host $siteUsers -ForegroundColor Blue
