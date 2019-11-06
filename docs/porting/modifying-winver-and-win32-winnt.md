---
title: Aktualizace WINVER a _WIN32_WINNT
ms.date: 09/04/2017
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: 0cfdb3d065a85bd02ef21de9c4c5282cf54fcb2a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627261"
---
# <a name="update-winver-and-_win32_winnt"></a>Aktualizace WINVER a _WIN32_WINNT

Vizuál C++ už nepodporuje cílení na Windows 95, Windows 98, Windows Millennium, Windows NT nebo Windows 2000. Pokud jsou makra **WINVER** nebo **_WIN32_WINNT** přiřazena k některé z těchto verzí systému Windows, je nutné upravit makra. Pokud upgradujete projekt, který byl vytvořen pomocí dřívější verze vizuálu C++, může dojít k chybám kompilace souvisejících s makry **WINVER** nebo **_WIN32_WINNT** , pokud jsou přiřazeny k verzi systému Windows, která již není podporována.

## <a name="remarks"></a>Poznámky

Chcete-li upravit makra v souboru hlaviček (například targetver. h, který je zahrnut při vytváření projektu, který cílí na systém Windows), přidejte následující řádky.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Cílí na operační systém Windows 10. Tyto hodnoty jsou uvedeny v souboru hlaviček systému Windows souboru SDKDDKVer. h, který také definuje makra pro jednotlivé verze systému Windows. Před zahrnutím souboru SDKDDKVer. h byste měli přidat příkaz #define. Tady jsou řádky z verze souboru SDKDDKVer. h pro Windows 10, které zakódují hodnoty pro jednotlivé verze Windows:

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

Pokud nevidíte všechny tyto verze Windows uvedené na kopii souboru SDKDDKVer. h, pravděpodobně používáte starší verzi Windows SDK. Projekty Win32 v sadě Visual Studio 2017 ve výchozím nastavení používají sadu Windows 10 SDK.

> [!NOTE]
> Pokud zahrnete do své aplikace interní hlavičky MFC, hodnoty nejsou zaručené pro práci.

Toto makro lze definovat také pomocí možnosti kompilátoru `/D`. Další informace naleznete v tématu [/d (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md).

Další informace o významu těchto maker naleznete v tématu [using the Windows Headers](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Viz také:

[Historie C++ vizuálních změn](../porting/visual-cpp-change-history-2003-2015.md)
