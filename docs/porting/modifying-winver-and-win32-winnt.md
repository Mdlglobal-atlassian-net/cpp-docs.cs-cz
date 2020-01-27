---
title: Aktualizace maker WINVER a _WIN32_WINNT
description: Kdy a jak aktualizovat makra WINVER a _WIN32_WINNT v upgradovaných projektech sady C++ Visual Studio.
ms.date: 01/22/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: b81c7967732c7b0c23ff0eb73d2a866a9b33713b
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725693"
---
# <a name="update-winver-and-_win32_winnt"></a>Aktualizace maker WINVER a _WIN32_WINNT

Při použití Windows SDK můžete určit, ve kterých verzích Windows může běžet váš kód. Makra preprocesoru **WINVER** a **_WIN32_WINNT** určují minimální verzi operačního systému, kterou váš kód podporuje. Visual Studio a podpora kompilátoru C++ Microsoftu cílí na Windows 7 SP1 a novější. Starší sady nástrojů obsahují podporu pro Windows XP SP4, Windows Server 2003 SP4, Vista a Windows Server 2008. Systémy Windows 95, Windows 98, Windows MILLENNIUM, Windows NT a Windows 2000 nejsou podporovány.

Při upgradu staršího projektu může být nutné aktualizovat makra **WINVER** nebo **_WIN32_WINNT** . Pokud jsou přiřazeny hodnoty pro nepodporovanou verzi systému Windows, mohou se zobrazit chyby kompilace související s těmito makry.

## <a name="remarks"></a>Poznámky

Chcete-li upravit makra v souboru hlaviček (například v *targetver. h*, který je součástí některých šablon projektů cílících na systém Windows), přidejte následující řádky.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Makra v příkladu jsou nastavena na cílení na všechny verze operačního systému Windows 10. Možné hodnoty jsou uvedeny v souboru hlaviček systému Windows *souboru SDKDDKVer. h*, který definuje makra pro každou hlavní verzi systému Windows. Chcete-li sestavit aplikaci pro podporu předchozí platformy Windows, přidejte *soubor WinSDKVer. h*. Potom nastavte makra **WINVER** a **_WIN32_WINNT** na nejstarší podporovanou platformu před zahrnutím *souboru SDKDDKVer. h*. Tady jsou řádky z verze sady Windows 10 SDK *souboru SDKDDKVer. h* , které zakódují hodnoty pro jednotlivé hlavní verze systému Windows:

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

Pro přesnější přístup k verzím můžete použít konstanty verze NTDDI v *souboru SDKDDKVer. h*. Tady jsou některá makra definovaná v *souboru SDKDDKVer. h* ve Windows 10 SDK verze 10.0.18362.0:

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

Makra **OSVER**, **SPVER**a **SUBVER** lze použít ve vašem kódu k řízení podmíněné kompilace pro různé úrovně podpory rozhraní API.

Nesmíte Zobrazit všechny tyto verze Windows uvedené na *souboru SDKDDKVer. h* , na které se díváte. To znamená, že pravděpodobně používáte starší verzi Windows SDK. Ve výchozím nastavení používají nové projekty Windows v sadě Visual Studio sadu Windows 10 SDK.

> [!NOTE]
> Pokud zahrnete do své aplikace interní hlavičky MFC, hodnoty nejsou zaručené pro práci.

Toto makro lze definovat také pomocí možnosti kompilátoru `/D`. Další informace naleznete v tématu [/d (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md).

Další informace o významu těchto maker naleznete v tématu [using the Windows Headers](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Viz také:

[Historie C++ vizuálních změn](../porting/visual-cpp-change-history-2003-2015.md)
