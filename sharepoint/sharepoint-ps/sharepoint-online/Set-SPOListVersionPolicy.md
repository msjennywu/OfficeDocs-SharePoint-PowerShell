---
external help file: sharepointonline.xml
Module Name: Microsoft.Online.SharePoint.PowerShell
online version: https://learn.microsoft.com/powershell/module/sharepoint-online/set-spolistversionpolicy
applicable: SharePoint Online
title: Set-SPOListVersionPolicy
schema: 2.0.0
author: msjennywu
ms.author: jennywu
ms.reviewer:
manager: seanmc
---

# Set-SPOListVersionPolicy

## SYNOPSIS

Sets the version policy setting on the cocument library.

## SYNTAX

```powershell
Set-SPOListVersionPolicy [-Site] <SpoSitePipeBind>
 [-List] <SpoListPipeBind>
 [-EnableAutoExpirationVersionTrim <Boolean>]
 [-MajorVersionLimit <int>]
 [-MajorWithMinorVersionsLimit <int>]
 [-ExpireVersionsAfterDays <int>]
 [<CommonParameters>]
```

## DESCRIPTION

Sets the version policy setting on the document library.

## EXAMPLES

### Example 1
```powershell
Set-SPOListVersionPolicy -Site https://contoso.sharepoint.com/sites/site1 -List "Documents" -EnableAutoExpirationVersionTrim $true
```
Example 1 sets Automatic version Storage Limits on the document library.

### EXAMPLE 2

```powershell
Set-SPOListVersionPolicy -Site https://contoso.sharepoint.com/sites/site1 -List "Documents" -EnableAutoExpirationVersionTrim $false -MajorVersionLimit 500 -MajorWithMinorVersionsLimit 20 -ExpireVersionsAfterDays 30
```

Example 2 sets Manual Version Storage Limits on the document library by limiting the number of versions and the time (in days) versions are kept.

### EXAMPLE 3

```powershell
Set-SPOListVersionPolicy -Site https://contoso.sharepoint.com/sites/site1 -List "Documents" -EnableAutoExpirationVersionTrim $false -MajorVersionLimit 500 -MajorWithMinorVersionsLimit 20 -ExpireVersionsAfterDays 0
```

Example 3 sets Manual Version Storage Limits on the document library by limiting the number of versions with no time limits. The new document libraries will use this version setting.

## PARAMETERS

### -Site

Specifies the URL of the site.

```yaml
Type: SpoSitePipeBind
Parameter Sets: (All)
Aliases:
Applicable: SharePoint Online
Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -List

The document library name or Id.

```yaml
Type: SPOListPipeBind
Parameter Sets: (All)

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAutoExpirationVersionTrim
Global and SharePoint admins in Microsoft 365 can set Document Library level Version History Limit settings that universally apply to new versions created.

When Version History Limits are managed Automatically, SharePoint employs an algorithm behind the scenes that deletes (thins out) intermittent older versions that are least likely to be needed, while preserving sufficient high-value versions - more versions in the recent past and fewer farther back in time - in case restores are required.

The valid values are:

- True - Version History Limits for new versions created on the Document Library will be managed Automatically.
- False - Version History Limits for new Versions created on the Document Library will be managed Manually by setting limits to the number of major versions (MajorVersionLimit), number of major with minor versions (MajorWithMinorVersionsLimit) and time set (ExpireVersionsAfterDays).  Review the documentation of both parameters to manage your organization's version limits Manually.  

> [!NOTE]
> When Version History Limits are managed Manually (EnableAutoExpirationVersionTrim $false), MajorVersionLimit, MajorWithMinorVersionsLimit and ExpireVersionsAfterDays are required parameters with the following acceptable values:
> a. MajorVersionLimit accepts values from 1 through 50,000 (inclusive).
> b. MajorWithMinorVersionsLimit accepts values from 0 through 50,000 (inclusive).
> c. ExpireVersionsAfterDays accepts values of 0 to Never Expire or values >= 30 to delete versions that exceed that time period.
> When Version History Limits are managed Automatically (EnableAutoExpirationVersionTrim $true), setting MajorVersionLimit or ExpireVersionsAfterDays will result in an error as the count limits are set by the service.

PARAMVALUE: $true | $false

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:
Applicable: SharePoint Online
Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MajorVersionLimit
When Version History Limits are managed Manually (EnableAutoExpirationVersionTrim $false), admins will need to set the limits to the number of major versions (MajorVersionLimit) and the time period the versions are stored (ExpireVersionsAfterDays). Please check the description of EnableAutoExpirationVersionTrim for more details.

PARAMVALUE: Int32

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:
Applicable: SharePoint Online
Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MajorWithMinorVersionsLimit
When Version History Limits are managed Manually (EnableAutoExpirationVersionTrim $false), admins will need to set the limits to the number of major versions (MajorVersionLimit), the number of major with minor versions (MajorWithMinorVersionsLimit) and the time period the versions are stored (ExpireVersionsAfterDays). Please check the description of EnableAutoExpirationVersionTrim for more details.

PARAMVALUE: Int32

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:
Applicable: SharePoint Online
Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExpireVersionsAfterDays
When Version History Limits are managed Manually (EnableAutoExpirationVersionTrim $false), admins will need to set the limits to the number of major versions (MajorVersionLimit), the number of major with minor versions (MajorWithMinorVersionsLimit) and the time period the versions are stored (ExpireVersionsAfterDays). Please check the description of EnableAutoExpirationVersionTrim for more details.

PARAMVALUE: Int32

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:
Applicable: SharePoint Online
Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## RELATED LINKS

[Getting started with SharePoint Online Management Shell](https://learn.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Get-SPOListVersionPolicy](Get-SPOListVersionPolicy.md)