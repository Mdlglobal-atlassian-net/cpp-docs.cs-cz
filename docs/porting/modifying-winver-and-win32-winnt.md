---
title: "Úpravy maker WINVER a _WIN32_WINNT | Microsoft Docs"
ms.custom: 
ms.date: 09/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- WINVER in an upgraded Visual C++ project
- _WIN32_WINNT in an upgraded Visual C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6787786022d0cc58fae6b4510a3675f0da21ba6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="modifying-winver-and-win32winnt"></a>Úpravy maker WINVER a _WIN32_WINNT

Visual C++ již nepodporuje cílení systému Windows 95, Windows 98, Windows ME, Windows NT nebo Windows 2000. Pokud vaše **WINVER** nebo **_WIN32_WINNT** makra se přiřadí k jednomu z těchto verzí systému Windows, musíte upravit makra. Při upgradu na projekt, který byl vytvořen pomocí dřívější verze aplikace Visual C++, mohou se zobrazit chyby při kompilaci související s **WINVER** nebo **_WIN32_WINNT** makra, pokud jsou přiřazena k verzi Windows, která již není podporována.  
  
## <a name="remarks"></a>Poznámky  

Pokud chcete upravit makra, v záhlaví souboru (například targetver.h která je součástí při vytváření projektu, jehož cílem Windows), přidejte následující řádky.  
  
```C  
#define WINVER 0x0A00  
#define _WIN32_WINNT 0x0A00  
```  
  
To cílí operačním systémem Windows 10. Tyto hodnoty jsou uvedeny v záhlaví souboru Windows SDKDDKVer.h, který definuje také makra pro každou verzi systému Windows. Měli byste přidat #define příkazu před zahrnutím SDKDDKVer.h. Zde jsou řádky z Windows 10 verzi SDKDDKVer.h, které kódování hodnoty pro jednotlivé verze Windows:  
  
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
  
Pokud nevidíte, že všechny tyto verze systému Windows uvedené v kopii SDKDDKVer.h, který se díváte na, pravděpodobně používáte starší verze sady Windows SDK. Ve výchozím nastavení používají Win32 projektů Visual Studio 2017 Windows 10 SDK.   
  
> [!NOTE]
>  Hodnoty nemusí fungovat, pokud patří interní hlavičky MFC ve vaší aplikaci.  
  
Toto makro můžete také definovat pomocí **/D** – možnost kompilátoru. Další informace najdete v tématu [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md).  
  
Další informace o význam těchto maker najdete v tématu [použití Windows hlaviček](https://msdn.microsoft.com/library/windows/desktop/aa383745).  
  
## <a name="see-also"></a>Viz také  

[Historie změn Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)