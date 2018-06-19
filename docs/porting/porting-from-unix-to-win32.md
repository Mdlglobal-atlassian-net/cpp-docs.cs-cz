---
title: Portování ze systému UNIX do Win32 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 628d032ff00205b3f511a613a866f025d62dc50a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843285"
---
# <a name="porting-from-unix-to-win32"></a>Portování ze systému UNIX do Win32
Při migraci aplikací ze systému UNIX do systému Windows, máte několik možností:  
  
-   Použití knihovny systému UNIX do portu aplikací ze systému UNIX do Win32  
  
-   Portování aplikací ze systému UNIX do Win32 nativně  
  
-   Spouštění UNIX aplikací v systému Windows pomocí subsystému POSIX  
  
## <a name="unix-libraries"></a>Knihovny systému UNIX  
 Jednou z možností UNIX programátory normálně zvažte, je použití knihovny systému UNIX jako třetích stran umožníte jejich kompilace kódu UNIX jako spustitelného souboru Win32. Několik komerční (a alespoň jeden veřejné domény) knihovny to udělat. Toto je možnost pro některé aplikace. Tyto knihovny portování výhodou je, že minimalizují počáteční úsilí pro přenos. Hlavní nevýhodou pro konkurenční softwarový produkt, je, že nativního portu Win32 aplikace bude obecně rychlejší a bude mít nevyhnutelně další funkce. Může být nevhodných aplikace, který krok mimo její prostředí systému UNIX, pokud je potřeba provádět volání Win32 získat další power ze systému Windows.  
  
 Následující seznam uvádí Microsoft a třetích stran pro přenos a podpora migrace UNIX pro aplikaci Visual C++:  
  
### <a name="unix-migration-guides"></a>Příručky k migraci UNIX  
 Průvodce migrací UNIX vlastní aplikace obsahuje technickou nápovědu migrace kódu ze systému UNIX do Win32 prostředí.  
  
 [http://go.microsoft.com/fwlink/p/?linkid=95428](http://go.microsoft.com/fwlink/p/?linkid=95428)  
  
 Průvodce projektem migrace Unix doplňuje Průvodce migrací UNIX vlastní aplikace poskytnutím vysokoúrovňové pomoci s přenesením podstatných projektů ze systému UNIX do Win32. Průvodce poskytuje Rady na problémy, které je třeba zvážit v každé fázi migrace projektu. Průvodce může být stažen:  
  
 [http://go.microsoft.com/fwlink/p/?linkid=20012](http://go.microsoft.com/fwlink/p/?linkid=20012)  
  
### <a name="microsoft-windows-services-for-unix-sfu"></a>Služby Microsoft Windows pro UNIX (SFU)  
 Služby systému Windows pro UNIX (SFU) poskytuje celou řadu napříč platformami služby pro integraci systému Windows do existujících prostředí založené na systému UNIX. Služby pro systém UNIX poskytuje sdílení souborů, vzdálený přístup a správu, synchronizace hesel, společnou správu adresářů, společnou sadu nástrojů a prostředí.  
  
 [Služby systému Windows pro UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### <a name="interopsystemscom"></a>InteropSystems.com  
 [http://www.interopsystems.com/](http://www.interopsystems.com/)  
  
 Třetí straně lokality pro společnost poskytuje softwarem, který podporuje přenos ze systému UNIX do Win32.  
  
### <a name="c-boost-web-site"></a>Nárůst C++ webu  
 [http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)  
  
 [http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)  
  
## <a name="porting-unix-applications-directly-to-win32"></a>Přenos aplikací systému UNIX přímo do Win32  
 Další možností je portování aplikací systému UNIX do Win32 přímo. Pomocí knihovny ANSI C/C++ a komerčních knihoven kompilátoru C, mnoho tradiční systému, který volání spoléhali na aplikací pro systém UNIX jsou k dispozici v aplikace Win32.  
  
 Výstupní model **stdio**– na základě aplikací není potřeba změnit, protože konzole Win32 napodobovat rozhraní API **stdio** modelu a verze *curses* existovat využívající rozhraní API konzoly Win32. Další informace najdete v tématu [SetConsoleCursorPosition](http://msdn.microsoft.com/library/windows/desktop/ms686025).  
  
 Aplikace založené na soket Berkeley potřebují velmi málo změn fungovat jako aplikace Win32. Rozhraní Windows Sockets je navržené pro přenositelnost sokety BSD s minimálními změnami, které jsou popsány v úvodní části specifikace rozhraní WinSock.  
  
 Windows podporuje kompatibilní se standardem DCE RPC, takže jsou snadno použitelné aplikace založené na protokolu RPC. V tématu [RPC funkce](http://msdn.microsoft.com/library/windows/desktop/aa378623).  
  
 Jeden z největších oblasti rozdíl je v modelu procesu. Má UNIX **rozvětvení**; Win32 neexistuje. V závislosti na použití **rozvětvení** a základu kódu Win32 má dvě rozhraní API, které lze použít: **CreateProcess** a `CreateThread`. Aplikace systému UNIX, která větve, více kopií sám sebe může být přepracována ve Win32 více procesů nebo jeden proces s více vlákny. Pokud se používají více procesů, existují různé způsoby IPC, který slouží ke komunikaci mezi procesy (a případně aktualizaci kódu a data nový proces jako nadřazeným prvkem, pokud funkce, **rozvětvení** poskytuje je potřeba). Další informace o IPC, najdete v části [meziprocesová komunikace](http://msdn.microsoft.com/library/windows/desktop/aa365574).  
  
 Systém Windows a UNIX Grafické modely se příliš neliší. UNIX používá X okno systému grafické uživatelské rozhraní, zatímco Windows používá GDI. Když koncept podobný, není jednoduché mapování X API GDI rozhraní API. Podpora OpenGL je však k dispozici pro migrace založené na systému UNIX OpenGL aplikací. A existují X klienty a servery pro systém Windows X. V tématu [kontexty zařízení](http://msdn.microsoft.com/library/windows/desktop/dd183553) informace o rozhraní GDI.  
  
 Základní aplikace systému UNIX, včetně mnoha aplikace CGI, měli snadno portu pro aplikaci Visual C++ v systému Windows. Funguje jako **otevřete**, `fopen`, **číst**, **zápisu** a ostatní jsou k dispozici v knihovně Visual C++ Runtime. Existuje také mapování 1: 1 mezi C UNIX rozhraní API a rozhraní API Win32: **otevřete** k **CreateFile**, **číst** k **ReadFile**, **zápisu** k **WriteFile**, `ioctl` k **DeviceIOControl**, **zavřete** k **CloseFile**a tak dále.  
  
## <a name="windows-posix-subsystem"></a>Subsystém POSIX systému Windows  
 Jiný možnost UNIX programátory pohled na je subsystému POSIX systému Windows. Však podporuje pouze POSIX 1003.1, která byla pouze verze POSIX standardizované při vytvoření systému Windows NT. Od té doby došlo malá poptávka po rozšíření tohoto subsystému, protože většina aplikací mít byl převeden na Win32. Systém 1003.1 je zajímavý pro plně funkční aplikace, protože neobsahuje řadu funkcí (například ty ve verzi 1003.2 sítě podporu a tak dále). Složité aplikace, spuštěné v subsystému Windows POSIX nemají přístup k funkcím Windows k dispozici pro aplikace Win32, jako jsou soubory mapované paměti, sítě a grafiky. Aplikace, jako je VI, LS a GREP jsou hlavním cílem pro subsystému POSIX systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce Visual C++ přenosem a upgradováním](visual-cpp-change-history-2003-2015.md)   
 [UNIX](../c-runtime-library/unix.md)   
 [Odvozená pravidla](../build/inference-rules.md)