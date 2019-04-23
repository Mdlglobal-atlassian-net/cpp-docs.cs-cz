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
ms.openlocfilehash: ac893981ff8c697dc090f1e6ad5ac61886a69f99
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035861"
---
# <a name="odbc-administrator"></a>Správce rozhraní ODBC

Správce rozhraní ODBC zaregistruje a nakonfiguruje [zdroje dat](../../data/odbc/data-source-odbc.md) k dispozici, místně nebo v síti. Vytvořit kód ve svých aplikacích, které vaši uživatelé připojí ke zdrojům dat pomocí průvodců informace poskytnuté správcem rozhraní ODBC.

Nastavení zdroje dat rozhraní ODBC pro třídy knihovny MFC rozhraní ODBC nebo třídy knihovny MFC objektu pro přístup k datům (DAO), musíte nejprve zaregistrovat a konfigurace zdroje dat. Přidání a odebrání zdrojů dat pomocí Správce rozhraní ODBC. V závislosti na ovladač ODBC můžete také vytvořit nové zdroje dat.

Správce rozhraní ODBC je nainstalovat během instalace. Pokud jste zvolili **vlastní** instalace a nevybrali žádné ovladače rozhraní ODBC v **možnosti databáze** dialogové okno, musíte spustit instalaci znovu a nainstalujte potřebné soubory.

Během instalace si můžete vybrat ovladače rozhraní ODBC, které chcete nainstalovat. Později můžete nainstalovat další ovladače, které se dodávají s jazykem Visual C++ pomocí programu instalace aplikace Visual C++.

Pokud chcete instalaci ovladače rozhraní ODBC, které se nedodává s jazykem Visual C++, musíte spustit instalační program, který doprovází ovladače.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Chcete-li nainstalovat ovladače rozhraní ODBC, které se dodávají s jazykem Visual C++

1. Spusťte instalaci z disku CD-ROM distribuce Visual C++.

   Otevírání dialogové okno instalačního programu se zobrazí.

1. Klikněte na tlačítko **Další** v každém dialogovém, dokud se nedostanete **možnosti instalace** dialogové okno. Vyberte **vlastní**a potom klikněte na tlačítko **Další**.

1. Zrušte zaškrtnutí všech políček v **instalace Microsoft Visual C++** dialogové okno s výjimkou **možnosti databáze** zaškrtněte políčko a potom klikněte na tlačítko **podrobnosti** zobrazíte **Možnosti databáze** dialogové okno.

1. Zrušte **Microsoft Data Access Objects** zaškrtněte políčko **ovladače ODBC Microsoft** zaškrtněte políčko a potom klikněte na tlačítko **podrobnosti**.

   **Ovladače ODBC Microsoft** zobrazí se dialogové okno.

1. Vyberte ovladače, kterou chcete nainstalovat a potom klikněte na **OK** dvakrát.

1. Klikněte na tlačítko **Další** na zbývajících dialogových oknech a spusťte tak instalaci. Instalační program vás upozorní, když je instalace dokončena.

Při instalaci ovladače, můžete nakonfigurovat zdroj dat pomocí Správce rozhraní ODBC. Ikona ODBC zjistíte v Ovládacích panelech.

## <a name="see-also"></a>Viz také:

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)