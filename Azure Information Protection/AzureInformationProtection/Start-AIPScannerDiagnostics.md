---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137317
schema: 2.0.0
---

# Start-AIPScannerDiagnostics

## SYNOPSIS
**Relevant for:** Unified labeling client only

Starts a series of health checks for a locally installed AIP scanner service.

## SYNTAX

```
Start-AIPScannerDiagnostics [-OnBehalfOf <PSCredential>] [-ResetConfig] [-VerboseErrorCount <integer>] [<CommonParameters>]
```

## DESCRIPTION
The **Start-AIPScannerDiagnostics** cmdlet triggers a series of diagnostic checks to verify that the scanner deployment is healthy.

Diagnostic checks include whether:

- The database is up-to-date and accessible
- URLs are accessible
- An authentication token is found and the policy can be acquired
- The profile is set in the Azure portal
- Offline/online configuration exists and can be acquired
- Rules are valid

## EXAMPLES

### Example 1: Starts the diagnostic tool for a locally installed AIP scanner
```powershell
PS C:\> $scanner_account_creds= Get-Credential
PS C:\> Start-AIPScannerDiagnostics -OnBehalfOf $scanner_account_creds
```

This example prompts you to enter credentials for a specific account, and then provide the credentials of the service account used to run the AIP scanner service.

### Example 2: Starts the diagnostic tool with a large number of errors printed from the scanner log
```powershell
PS C:\> $scanner_account_creds= Get-Credential
PS C:\> Start-AIPScannerDiagnostics -OnBehalfOf $scanner_account_creds -Verbose -VerboseErrorCount 30
```

This example prompts you to enter credentials for a specific account, and then provide the credentials of the service account used to run the AIP scanner service. The last 30 errors are printed from the scanner log.
## PARAMETERS

### -OnBehalfOf
Defines the scanner where you want to run the diagnostics, when you are running the command under a user that is not the scanner user.

The **OnBehalfOf** value defines the variable that holds a credentials object. The diagnostics checks are run on the AIP scanner for the account defined by that credentials object.

Use the [Get-Credential](/powershell/module/microsoft.powershell.security/get-credential) cmdlet to get the variable that stores your credentials.

> [!NOTE]
> If you are running the command under the scanner user, this parameter is not required. 
> 

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResetConfig
Resets the policy cache. When used, the policy is refreshed even if the last refresh occurred less than four hours ago.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VerboseErrorCount
Relevant only when the **Verbose** parameter is used in the command.

Defines the number of errors you want to see printed from the scanner log, if you want to print a number of errors other than the default of 10.


```yaml
Type: Integer
Parameter Sets: (All)
Aliases:
Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.

> [!NOTE]
> For this cmdlet, the **Verbose** parameter prints the last 10 errors from the scanner log. To change the number of errors printed, use the **VerboseErrorCount** parameter
> 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

### System.Object

## NOTES
- This cmdlet requires you to define a specific scanner account in the **-OnBehalfOf** parameter. The OnBehalfOf parameter requires you to run your PowerShell session as an Administrator.

- Diagnostic checks do check for scanner deployment prerequisites. This cmdlet is supported only after you have the scanner deployed and your [profile configured](/azure/information-protection/deploy-aip-scanner#install-the-scanner).

    For more information, see [Deploying the Azure Information Protection scanner](/azure/information-protection/deploy-aip-scanner).

## RELATED LINKS
[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Stop-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](Update-AIPScanner.md)
