---
title: "-CLRSUPPORTLASTERROR (zachovat poslední kód chyby pro volání PInvoke) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRSUPPORTLASTERROR
dev_langs:
- C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e082637e25832c5c5036910f7b67aff53d867bdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke)
**/ CLRSUPPORTLASTERROR**, který je ve výchozím, uchovává kód poslední chyby funkcí zavolaném prostřednictvím P/Invoke mechanismus, který umožňuje volání nativních funkcí ze kódu v knihovnách DLL, kompilovat s **/CLR**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## <a name="remarks"></a>Poznámky  
 Zachovat poslední kód chyby znamená snížení výkonu.  Pokud nechcete zabývat dopad na výkon systému zachovat poslední kód chyby, propojit s **/CLRSUPPORTLASTERROR:NO**.  
  
 Můžete minimalizovat dopad na výkon pomocí propojení s **/CLRSUPPORTLASTERROR:SYSTEMDLL**, poslední kód chyby pro funkce, která zachová jenom v systémové knihovny DLL.  Systémová knihovna DLL je definován jako jednu z těchto možností:  
  
|||||  
|-|-|-|-|  
|SE. KNIHOVNY DLL|ACTIVEDS. KNIHOVNY DLL|ADPTIF. KNIHOVNY DLL|ADVAPI32. KNIHOVNY DLL|  
|ASYCFILT. KNIHOVNY DLL|AUTHZ. KNIHOVNY DLL|AVICAP32. KNIHOVNY DLL|AVIFIL32. KNIHOVNY DLL|  
|SOUBOR CAB. KNIHOVNY DLL|CLUSAPI. KNIHOVNY DLL|COMCTL32. KNIHOVNY DLL|COMDLG32. KNIHOVNY DLL|  
|COMSVCS. KNIHOVNY DLL|CREDUI. KNIHOVNY DLL|CRYPT32. KNIHOVNY DLL|CRYPTNET. KNIHOVNY DLL|  
|CRYPTUI. KNIHOVNY DLL|D3D8THK. KNIHOVNY DLL|DBGENG. KNIHOVNY DLL|DBGHELP. KNIHOVNY DLL|  
|DCIMAN32. KNIHOVNY DLL|DNSAPI. KNIHOVNY DLL|DSPROP. KNIHOVNY DLL|DSUIEXT. KNIHOVNY DLL|  
|SOUBORU GDI32. KNIHOVNY DLL|GLU32. KNIHOVNY DLL|KNIHOVNA HLINK. KNIHOVNY DLL|ICM32. KNIHOVNY DLL|  
|IMAGEHLP. KNIHOVNY DLL|IMM32. KNIHOVNY DLL|IPHLPAPI. KNIHOVNY DLL|IPROP. KNIHOVNY DLL|  
|KERNEL32. KNIHOVNY DLL|KSUSER. KNIHOVNY DLL|LOADPERF. KNIHOVNY DLL|LZ32. KNIHOVNY DLL|  
|MAPI32. KNIHOVNY DLL|MGMTAPI. KNIHOVNY DLL|PŘÍKAZ MOBSYNC. KNIHOVNY DLL|MPR. KNIHOVNY DLL|  
|MPRAPI. KNIHOVNY DLL|MQRT. KNIHOVNY DLL|MSACM32. KNIHOVNY DLL|MSCMS. KNIHOVNY DLL|  
|MSI. KNIHOVNY DLL|MSIMG32. KNIHOVNY DLL|MSRATING. KNIHOVNY DLL|MSTASK. KNIHOVNY DLL|  
|MSVFW32. KNIHOVNY DLL|MSWSOCK. KNIHOVNY DLL|MTXEX. KNIHOVNY DLL|NDDEAPI. KNIHOVNY DLL|  
|NETAPI32. KNIHOVNY DLL|NPPTOOLS. KNIHOVNY DLL|ROZHRANÍ NTDSAPI. KNIHOVNY DLL|NTDSBCLI. KNIHOVNY DLL|  
|NTMSAPI. KNIHOVNY DLL|ODBC32. KNIHOVNY DLL|ODBCBCP. KNIHOVNY DLL|OLE32. KNIHOVNY DLL|  
|OLEACC. KNIHOVNY DLL|OLEAUT32. KNIHOVNY DLL|OLEDLG. KNIHOVNY DLL|OPENGL32. KNIHOVNY DLL|  
|PDH. KNIHOVNY DLL|SOUBOR POWRPROF. KNIHOVNY DLL|QOSNAME. KNIHOVNY DLL|DOTAZ. KNIHOVNY DLL|  
|RASAPI32. KNIHOVNY DLL|RASDLG. KNIHOVNY DLL|RASSAPI. KNIHOVNY DLL|RESUTILS. KNIHOVNY DLL|  
|RICHED20. KNIHOVNY DLL|RPCNS4. KNIHOVNY DLL|RPCRT4. KNIHOVNY DLL|RTM. KNIHOVNY DLL|  
|RTUTILS. KNIHOVNY DLL|SCARDDLG. KNIHOVNY DLL|SECUR32. KNIHOVNY DLL|SENSAPI. KNIHOVNY DLL|  
|SETUPAPI. KNIHOVNY DLL|SFC. KNIHOVNY DLL|SHELL32. KNIHOVNY DLL|SHFOLDER. KNIHOVNY DLL|  
|SHLWAPI. KNIHOVNY DLL|SISBKUP. KNIHOVNY DLL|SNMPAPI. KNIHOVNY DLL|SRCLIENT. KNIHOVNY DLL|  
|STÁTNÍ DAŇ. KNIHOVNY DLL|TAPI32. KNIHOVNY DLL|PROVOZ. KNIHOVNY DLL|ADRESA URL. KNIHOVNY DLL|  
|URLMON. KNIHOVNY DLL|USER32. KNIHOVNY DLL|USERENV. KNIHOVNY DLL|USP10. KNIHOVNY DLL|  
|UXTHEME. KNIHOVNY DLL|VDMDBG. KNIHOVNY DLL|VERZE. KNIHOVNY DLL|WINFAX. KNIHOVNY DLL|  
|WINHTTP. KNIHOVNY DLL|WININET. KNIHOVNY DLL|WINMM. KNIHOVNY DLL|WINSCARD. KNIHOVNY DLL|  
|WINTRUST. KNIHOVNY DLL|WLDAP32. KNIHOVNY DLL|WOW32. KNIHOVNY DLL|WS2_32.DLL|  
|WSNMP32. KNIHOVNY DLL|WSOCK32.DLL|WTSAPI32. KNIHOVNY DLL|XOLEHLP. KNIHOVNY DLL|  
  
> [!NOTE]
>  Nespravované funkce, které se spotřebovávají kódem CLR ve stejném modulu nepodporuje zachování poslední chyby.  
  
-   Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje nativní knihovny DLL pomocí jeden exportované funkce, která upraví poslední chyba.  
  
```  
// CLRSUPPORTLASTERROR_dll.cpp  
// compile with: /LD  
#include <windows.h>  
#include <math.h>  
  
#pragma unmanaged  
__declspec(dllexport) double MySqrt(__int64 n) {  
   SetLastError(DWORD(-1));  
   return sqrt(double(n));  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad využívá knihovnu DLL, který ukazuje, jak používat **/CLRSUPPORTLASTERROR**.  
  
```  
// CLRSUPPORTLASTERROR_client.cpp  
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll  
// processor: x86  
#include <windows.h>  
#include <wininet.h>  
#include <stdio.h>  
#include <math.h>  
  
#pragma comment(lib, "wininet.lib")  
  
double MySqrt(__int64 n);  
  
#pragma managed  
int main() {  
   double   d = 0.0;  
   __int64 n = 65;  
   HANDLE  hGroup = NULL;  
   GROUPID groupID;  
   DWORD   dwSet = 127, dwGet = 37;  
  
   SetLastError(dwSet);  
   d = MySqrt(n);  
   dwGet = GetLastError();  
  
   if (dwGet == DWORD(-1))  
      printf_s("GetLastError for application call succeeded (%d).\n",  
             dwGet);  
   else  
      printf_s("GetLastError for application call failed (%d).\n",  
             dwGet);  
  
   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,  
                           0, 0, &groupID, 0);  
   dwGet = GetLastError();  
   if (dwGet == 183)  
      printf_s("GetLastError for system call succeeded (%d).\n",  
             dwGet);  
   else  
      printf_s("GetLastError for system call failed (%d).\n",  
             dwGet);  
}  
```  
  
```Output  
GetLastError for application call failed (127).  
GetLastError for system call succeeded (183).  
```  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)