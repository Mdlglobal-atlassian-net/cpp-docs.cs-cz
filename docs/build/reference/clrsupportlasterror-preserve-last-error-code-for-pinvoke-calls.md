---
title: /CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 64948d81759d415245e741bc6152d56bb35480d2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988349"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke)

**/CLRSUPPORTLASTERROR**, která je ve výchozím nastavení zapnutá, zachovává poslední chybový kód funkcí volaných pomocí mechanismu volání nespravovaného kódu, který umožňuje volat nativní funkce v knihovnách DLL z kódu zkompilovaného s možností **/CLR**.

## <a name="syntax"></a>Syntaxe

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Poznámky

Zachování kódu poslední chyby implikuje snížení výkonu.  Pokud nechcete mít dopad na výkon při zachování posledního kódu chyby, propojte pomocí **/CLRSUPPORTLASTERROR: No**.

Dopad na výkon můžete minimalizovat propojením s **/CLRSUPPORTLASTERROR: SYSTEMDLL**, který zachovává jenom poslední kód chyby pro funkce v systémových knihovnách DLL.  Systémová knihovna DLL je definována jako jedna z následujících:

|||||
|-|-|-|-|
|ACLUI.DLL|ACTIVEDS. DLL|ADPTIF.DLL|ADVAPI32.DLL|
|ASYCFILT. DLL|Přes. DLL|AVICAP32.DLL|AVIFIL32.DLL|
|Skříně. DLL|CLUSAPI.DLL|COMCTL32.DLL|COMDLG32.DLL|
|COMSVCS.DLL|CREDUI.DLL|CRYPT32.DLL|CRYPTNET.DLL|
|CRYPTUI.DLL|D3D8THK.DLL|DBGENG. DLL|DBGHELP.DLL|
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP. DLL|DSUIEXT.DLL|
|GDI32.DLL|GLU32.DLL|Knihovna. DLL|ICM32.DLL|
|Imagehlp. DLL|IMM32.DLL|IPHLPAPI.DLL|IPROP. DLL|
|KERNEL32.DLL|KSUSER.DLL|LOADPERF.DLL|LZ32.DLL|
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC.DLL|MPR.DLL|
|MPRAPI.DLL|MQRT.DLL|MSACM32.DLL|MSCMS.DLL|
|MSI.DLL|MSIMG32.DLL|MSRATING. DLL|MSTASK. DLL|
|MSVFW32.DLL|MSWSOCK. DLL|MTXEX.DLL|NDDEAPI.DLL|
|NETAPI32.DLL|NPPTOOLS. DLL|NTDSAPI.DLL|NTDSBCLI.DLL|
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32.DLL|
|OLEACC.DLL|OLEAUT32.DLL|OLEDLG. DLL|OPENGL32.DLL|
|PDH.DLL|POWRPROF. DLL|QOSNAME. DLL|Zadávání. DLL|
|RASAPI32.DLL|RASDLG. DLL|RASSAPI.DLL|RESUTILS.DLL|
|RICHED20.DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|
|RTUTILS.DLL|SCARDDLG. DLL|SECUR32.DLL|SENSAPI.DLL|
|SETUPAPI.DLL|SFC.DLL|Knihovny. DLL|SHFOLDER. DLL|
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT. DLL|
|STI.DLL|TAPI32.DLL|Prostřednictvím. DLL|Adresa URL. DLL|
|Urlmon. DLL|USER32.DLL|Souboru. DLL|USP10.DLL|
|UXTHEME. DLL|VDMDBG.DLL|Znění. DLL|WINFAX. DLL|
|WINHTTP.DLL|Souvisejících. DLL|WINMM. DLL|WINSCARD.DLL|
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2_32.DLL|
|WSNMP32. DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|

> [!NOTE]
>  Zachování poslední chyby není podporováno pro nespravované funkce, které jsou spotřebovány kódem CLR ve stejném modulu.

- Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **linker** .

1. Klikněte na stránku vlastností **příkazový řádek** .

1. Zadejte možnost do pole **Další možnosti** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Příklad

Následující příklad definuje nativní knihovnu DLL s jednou exportovanou funkcí, která upravuje poslední chybu.

```cpp
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

Následující ukázka používá knihovnu DLL, která demonstruje použití **/CLRSUPPORTLASTERROR**.

```cpp
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

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
