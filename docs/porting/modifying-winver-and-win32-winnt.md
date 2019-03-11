---
title: Úpravy maker WINVER a _WIN32_WINNT
ms.date: 09/04/2017
helpviewer_keywords:
- WINVER in an upgraded Visual C++ project
- _WIN32_WINNT in an upgraded Visual C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: a936a54620590d4dc21f43acd50abdc49d77ffa8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748733"
---
# <a name="modifying-winver-and-win32winnt"></a>Úpravy maker WINVER a _WIN32_WINNT

Jazyk Visual C++ již podporuje cílení na Windows 95, Windows 98, Windows ME, Windows NT nebo Windows 2000. Pokud vaše **WINVER** nebo **_WIN32_WINNT** makra se přiřadí k jednomu z těchto verzí systému Windows, je třeba upravit makra. Když upgradujete projekt, který byl vytvořen pomocí dřívější verze aplikace Visual C++, může se zobrazit související se chyby při kompilaci **WINVER** nebo **_WIN32_WINNT** makra, pokud jsou přiřazeny k verzi Windows, který už není podporovaná.

## <a name="remarks"></a>Poznámky

Pokud chcete upravit makra, v hlavičkovém souboru (například targetver.h která je zahrnuta, když vytvoříte projekt, který cílí na Windows), přidejte následující řádky.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

To cílí na operační systém Windows 10. Tyto hodnoty jsou uvedeny v souboru hlaviček Windows souboru SDKDDKVer.h také definuje makra pro každou verzi Windows. Měli byste přidat #define příkazu před zahrnutím souboru SDKDDKVer.h. Zde jsou řádky z Windows 10 verzi souboru SDKDDKVer.h, které kódování hodnoty pro každou verzi Windows:

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

Pokud nevidíte všechny tyto verze Windows uvedené v kopii souboru SDKDDKVer.h, že se díváte na, pravděpodobně používáte starší verzi sady Windows SDK. Ve výchozím nastavení používají Windows 10 SDK projekty Win32 v sadě Visual Studio 2017.

> [!NOTE]
> Hodnoty nemusí fungovat, pokud jste do aplikace zahrnout interní hlaviček knihovny MFC.

Toto makro můžete také definovat pomocí `/D` – možnost kompilátoru. Další informace najdete v tématu [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md).

Další informace o význam těchto maker naleznete v tématu [pomocí hlavičky Windows](/windows/desktop/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Viz také:

[Historie změn Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
