---
title: -CLRSUPPORTLASTERROR (zachování kódu poslední chyby pro volání PInvoke) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRSUPPORTLASTERROR
dev_langs:
- C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a80adfe34677c15a36af96ac412b7934747e68bc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707444"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke)

**/ CLRSUPPORTLASTERROR**, který je ve výchozím, zachová poslední chybový kód funkcí zavolaném prostřednictvím mechanismu P/Invoke, který umožňuje volat nativní funkce v knihovnách DLL z kódu zkompilovaná **/CLR**.

## <a name="syntax"></a>Syntaxe

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Poznámky

Zachování kódu poslední chyby znamená snížení výkonu.  Pokud nechcete, budou účtovat dopad na výkon zachování kódu poslední chyby, propojte s **/CLRSUPPORTLASTERROR:NO**.

Můžete minimalizovat dopad na výkon díky propojení s **/CLRSUPPORTLASTERROR:SYSTEMDLL**, který pouze zachová poslední chybový kód pro funkce v systémové knihovny DLL.  Systémová knihovna DLL je definován jako jeden z následujících akcí:

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
|MAPI32. KNIHOVNY DLL|MGMTAPI. KNIHOVNY DLL|PŘÍKAZ MOBSYNC. KNIHOVNY DLL|PRAVIDLA ZÁSAD SPRÁVY. KNIHOVNY DLL|
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
|STI ARCHITEKTURY. KNIHOVNY DLL|TAPI32. KNIHOVNY DLL|PROVOZ. KNIHOVNY DLL|ADRESA URL. KNIHOVNY DLL|
|URLMON. KNIHOVNY DLL|USER32. KNIHOVNY DLL|USERENV. KNIHOVNY DLL|USP10. KNIHOVNY DLL|
|UXTHEME. KNIHOVNY DLL|VDMDBG. KNIHOVNY DLL|VERZE. KNIHOVNY DLL|WINFAX. KNIHOVNY DLL|
|WINHTTP. KNIHOVNY DLL|WININET. KNIHOVNY DLL|WINMM. KNIHOVNY DLL|WINSCARD. KNIHOVNY DLL|
|WINTRUST. KNIHOVNY DLL|WLDAP32. KNIHOVNY DLL|WOW32. KNIHOVNY DLL|WS2_32.DLL|
|WSNMP32. KNIHOVNY DLL|WSOCK32.DLL|WTSAPI32. KNIHOVNY DLL|XOLEHLP. KNIHOVNY DLL|

> [!NOTE]
>  Zachovat poslední chyba není podporována pro nespravované funkce, které se spotřebovávají CLR kódu ve stejném modulu.

- Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Příklad

Následující příklad definuje nativní knihovnu DLL pomocí jednoho exportované funkce, která upravuje poslední chyby.

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

Následující příklad využívá knihovnu DLL, který demonstruje použití **/CLRSUPPORTLASTERROR**.

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

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)