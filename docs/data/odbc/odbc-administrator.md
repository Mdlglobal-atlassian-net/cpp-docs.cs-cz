---
title: "Správce rozhraní ODBC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a7d60f11457e509ae67da83aa6bc589af1ce43a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-administrator"></a>Správce rozhraní ODBC
Správce rozhraní ODBC registruje a konfiguruje [zdroje dat](../../data/odbc/data-source-odbc.md) k dispozici místně nebo v síti. Vytvoření kódu v aplikacích, které vaši uživatelé připojí ke zdrojům dat pomocí průvodců informace poskytnuté správcem rozhraní ODBC.  
  
 Nastavit zdroje dat ODBC pro použití s třídy knihovny MFC nebo třídy MFC objekt DAO (Data Access), musíte nejprve registrovat a nakonfigurujte zdroj dat. K přidání a odebrání zdrojů dat použijte Správce rozhraní ODBC. V závislosti na ovladač ODBC můžete také vytvořit nové zdroje dat.  
  
 Správce rozhraní ODBC je nainstalována během instalace. Pokud jste zvolili **vlastní** instalace a nevybrali žádné ovladače ODBC v **možnosti databáze** dialogové okno, musíte spustit instalaci znovu a nainstalujte potřebné soubory.  
  
 Během instalace vybrat, které chcete instalaci ovladače ODBC. Později můžete nainstalovat další ovladače, které se dodávají spolu s Visual C++ pomocí Visual C++ instalační program.  
  
 Pokud chcete instalaci ovladače ODBC, které se nedodává s Visual C++, musíte spustit instalační program, který doprovází ovladač.  
  
#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>K instalaci ovladače ODBC, které jsou dodávány pomocí Visual C++  
  
1.  Spusťte instalaci z disku CD-ROM distribuční Visual C++.  
  
     Otevření dialogového okna v instalační program je se zobrazí.  
  
2.  Klikněte na tlačítko **Další** v každém dialogovém, dokud se nedostanete **možnosti instalace** dialogové okno. Vyberte **vlastní**a potom klikněte na `Next`.  
  
3.  Zrušte zaškrtnutí všech políček v **instalace Microsoft Visual C++** dialogové okno s výjimkou **možnosti databáze** zaškrtněte políčko a potom klikněte na **podrobnosti** zobrazíte **Možnosti databáze** dialogové okno.  
  
4.  Vymazat **Microsoft Data Access Objects** zaškrtněte políčko **ovladače ODBC Microsoft** zaškrtněte políčko a potom klikněte na **podrobnosti**.  
  
     **Ovladače ODBC Microsoft** zobrazí se dialogové okno.  
  
5.  Vyberte ovladače, které chcete nainstalovat a potom klikněte na **OK** dvakrát.  
  
6.  Klikněte na tlačítko **Další** na zbývajících dialogových oknech zahájíte instalaci. Instalační program vás upozorní, po dokončení instalace.  
  
 Při instalaci ovladačů, můžete nakonfigurovat zdroje dat pomocí Správce rozhraní ODBC. Ikona ODBC zjistíte v Ovládacích panelech.  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)