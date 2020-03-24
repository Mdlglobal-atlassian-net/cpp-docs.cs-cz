---
title: Správce rozhraní ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213159"
---
# <a name="odbc-administrator"></a>Správce rozhraní ODBC

Správce rozhraní ODBC registruje a konfiguruje [zdroje dat](../../data/odbc/data-source-odbc.md) , které jsou k dispozici místně nebo v síti. Průvodci používají informace poskytované správcem rozhraní ODBC k vytvoření kódu ve vašich aplikacích, které propojí vaše uživatele se zdroji dat.

Chcete-li nastavit zdroj dat ODBC pro použití buď s třídami knihovny MFC rozhraní ODBC, nebo s třídami objektů DAO (Data Access Access) knihovny MFC, je nutné nejprve zaregistrovat a nakonfigurovat zdroj dat. K přidání a odebrání zdrojů dat použijte Správce rozhraní ODBC. V závislosti na ovladači ODBC můžete také vytvořit nové zdroje dat.

Správce rozhraní ODBC je nainstalován během instalace. Pokud jste zvolili možnost **vlastní** instalace a v dialogovém okně **Možnosti databáze** jste nevybrali žádné ovladače rozhraní ODBC, je nutné znovu spustit instalační program a nainstalovat tak potřebné soubory.

Během instalace vyberte ovladače rozhraní ODBC, které chcete nainstalovat. Později můžete nainstalovat další ovladače, které se dodávají C++ s jazykem Visual C++ pomocí programu Visual Setup.

Chcete-li nainstalovat ovladače rozhraní ODBC, které nejsou dodávány s C++jazykem Visual, je nutné spustit instalační program, který doprovází ovladač.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Instalace ovladačů ODBC, které dodávají s jazykem VisualC++

1. Spusťte instalační program z vašeho C++ vizuálního disku CD.

   Zobrazí se dialogové okno pro otevření v instalačním programu.

1. V každém dialogovém okně klikněte na tlačítko **Další** , dokud se nedostanete do dialogového okna **Možnosti instalace** . Vyberte možnost **vlastní**a poté klikněte na tlačítko **Další**.

1. Zrušte zaškrtnutí všech políček v **dialogovém okně C++ Microsoft Visual Setup** , kromě **Možnosti databáze** , a potom klikněte na tlačítko **Podrobnosti** . zobrazí se dialogové okno **Možnosti databáze** .

1. Zrušte zaškrtnutí políčka **Microsoft Data Access Objects** , zaškrtněte políčko **ovladače Microsoft ODBC** a pak klikněte na **Podrobnosti**.

   Zobrazí se dialogové okno **ovladače Microsoft ODBC** .

1. Vyberte ovladače, které chcete nainstalovat, a pak dvakrát klikněte na **OK** .

1. Kliknutím na tlačítko **Další** ve zbývajících dialogových oknech spusťte instalaci. Po dokončení instalace vás instalační program upozorní.

Po instalaci ovladačů můžete nakonfigurovat zdroj dat pomocí Správce rozhraní ODBC. Ikona ODBC se nachází v Ovládacích panelech.

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)
