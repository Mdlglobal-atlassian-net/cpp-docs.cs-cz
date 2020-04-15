---
title: /CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322278"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke)

**/CLRSUPPORTLASTERROR**, který je ve výchozím nastavení zapnutý, zachová poslední kód chyby funkcí volaných prostřednictvím mechanismu P/Invoke, který umožňuje volat nativní funkce v DLLS z kódu kompilovaného pomocí **/clr**.

## <a name="syntax"></a>Syntaxe

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Poznámky

Zachování posledního kódu chyby znamená snížení výkonu.  Pokud nechcete, aby vliv na výkon zachování poslední kód chyby, odkaz s **/CLRSUPPORTLASTERROR:NO**.

Dopad na výkon můžete minimalizovat propojením s **parametrem /CLRSUPPORTLASTERROR:SYSTEMDLL**, který zachová pouze poslední kód chyby pro funkce v systémových knihovnách DLL.  Systémová dll je definována jako jedna z následujících položek:

|||||
|-|-|-|-|
|ACLUI. Knihovny dll|activeds. Knihovny dll|ADPTIF. Knihovny dll|ADVAPI32. Knihovny dll|
|ASYCFILT. Knihovny dll|AUTHZ. Knihovny dll|AVICAP32. Knihovny dll|AVIFIL32. Knihovny dll|
|Skříň. Knihovny dll|CLUSAPI. Knihovny dll|COMCTL32. Knihovny dll|COMDLG32. Knihovny dll|
|cs. Knihovny dll|CREDUI. Knihovny dll|KRYPTA32. Knihovny dll|Kryptonem. Knihovny dll|
|CRYPTUI. Knihovny dll|D3D8THK. Knihovny dll|DBGENG. Knihovny dll|DBGHELP. Knihovny dll|
|DCIMAN32. Knihovny dll|DNSAPI. Knihovny dll|DSPROP. Knihovny dll|DSUIEXT. Knihovny dll|
|GDI32. Knihovny dll|GLU32. Knihovny dll|HLINK. Knihovny dll|ICM32. Knihovny dll|
|IMAGEHLP. Knihovny dll|IMM32. Knihovny dll|IPHLPAPI. Knihovny dll|IPROP. Knihovny dll|
|JÁDRO32. Knihovny dll|KSUSER. Knihovny dll|NAKLÁDAČKAF. Knihovny dll|LZ32. Knihovny dll|
|MAPI32. Knihovny dll|MGMTAPI. Knihovny dll|MOBSYNC. Knihovny dll|Mpr. Knihovny dll|
|MPRAPI. Knihovny dll|MQRT. Knihovny dll|MSACM32. Knihovny dll|mscms. Knihovny dll|
|Msi. Knihovny dll|MSIMG32. Knihovny dll|MSRATING. Knihovny dll|MSTASK. Knihovny dll|
|MSVFW32. Knihovny dll|mswsock. Knihovny dll|mtxex. Knihovny dll|NDDEAPI. Knihovny dll|
|NETAPI32. Knihovny dll|npptools. Knihovny dll|Rozhraní NTDSAPI. Knihovny dll|NTDSBCLI. Knihovny dll|
|Rozhraní NTMSAPI. Knihovny dll|ODBC32. Knihovny dll|ODBCBCP. Knihovny dll|OLE32. Knihovny dll|
|OLEACC. Knihovny dll|OLEAUT32. Knihovny dll|OLEDLG. Knihovny dll|OPENGL32. Knihovny dll|
|Pdh. Knihovny dll|POWRPROF. Knihovny dll|QOSNAME. Knihovny dll|Dotazu. Knihovny dll|
|Rasapi32. Knihovny dll|RASDLG. Knihovny dll|ROZHRANÍ RASSAPI. Knihovny dll|OPĚTOVNÉ POUŽITÍ. Knihovny dll|
|RICHED20. Knihovny dll|RPCNS4. Knihovny dll|RPCRT4. Knihovny dll|Rtm. Knihovny dll|
|RTUTILS. Knihovny dll|SCARDDLG. Knihovny dll|Secur32. Knihovny dll|SENSAPI. Knihovny dll|
|SETUPAPI. Knihovny dll|Sfc. Knihovny dll|SHELL32. Knihovny dll|SHFolder. Knihovny dll|
|SHLWAPI. Knihovny dll|SISBKUP. Knihovny dll|SNMPAPI. Knihovny dll|SRCLIENT. Knihovny dll|
|Sti. Knihovny dll|ROZHRANÍ TAPI32. Knihovny dll|Provozu. Knihovny dll|Adresu url. Knihovny dll|
|URLMON. Knihovny dll|UŽIVATEL32. Knihovny dll|UŽIVATELENV. Knihovny dll|USP10. Knihovny dll|
|Uxtheme. Knihovny dll|VDMDBG. Knihovny dll|Verze. Knihovny dll|WINFAX. Knihovny dll|
|WINHTTP. Knihovny dll|Wininet. Knihovny dll|WINMM. Knihovny dll|WINSCARD. Knihovny dll|
|WINTRUST. Knihovny dll|WLDAP32. Knihovny dll|WOW32. Knihovny dll|WS2_32.DLL|
|WSNMP32. Knihovny dll|WSOCK32.DLL|WTSAPI32. Knihovny dll|XOLEHLP. Knihovny dll|

> [!NOTE]
> Zachování poslední chyby není podporováno pro nespravované funkce, které jsou spotřebovány kódem CLR ve stejném modulu.

- Další informace naleznete v tématu [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **Linker.**

1. Klepněte na stránku vlastností **příkazového řádku.**

1. Zadejte tuto možnost do pole **Další možnosti.**

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Příklad

Následující ukázka definuje nativní dll s jednou exportovnou funkcí, která upravuje poslední chybu.

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

Následující ukázka spotřebovává dll, ukazuje, jak používat **/CLRSUPPORTLASTERROR**.

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

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti propojovacího zařízení MSVC](linker-options.md)
