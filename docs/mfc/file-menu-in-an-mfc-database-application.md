---
title: "Nabídka soubor v databázových aplikacích MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51f630f5a3fe1ee5833ac2796ff2acb1841af4c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="file-menu-in-an-mfc-database-application"></a>Nabídka Soubor v databázových aplikacích MFC
Pokud jste vytvoření databázové aplikace MFC a nepoužívejte serializace, jak by měla můžete interpretovat otevřené, zavřete, uložit a uložit jako příkazů v nabídce soubor při neexistují žádné pokyny styl pro tuto otázku, zde je několik návrhů:  
  
-   Zcela Eliminujte příkaz Otevřít z nabídky soubor.  
  
-   Interpretovat otevřete příkaz jako "otevřete databáze" a zobrazit seznam zdrojů dat, které vaše aplikace rozpozná uživatele.  
  
-   Otevřete interpretovat jako, případně, "otevřete profil." Zachování otevřené pro otevření serializovaných souboru, ale použijte soubor pro uložení serializovaných dokument obsahující informace "profilu uživatele", například uživatelské předvolby, včetně svůj nebo jeho přihlašovacího ID (volitelně s vyloučením heslo) a data zdroje potvrdí nejvíce nedávno pracovali s.  
  
 Průvodce aplikací MFC podporuje vytváření aplikací s žádné související dokumentu příkazy nabídky soubor. Vyberte **databáze zobrazení bez podpory souboru** možnost **databáze podporují** stránky.  
  
 Interpretace příkazu v nabídce Soubor zvláštním způsobem, je nutné přepsat obslužné rutiny jeden nebo více příkazů, hlavně v vaší `CWinApp`-odvozené třídy. Například, pokud je zcela přepsat `OnFileOpen` (které implementuje `ID_FILE_OPEN` příkaz) rozumí "otevřenou databázi:"  
  
-   Nemůžete volat základní třída verzi `OnFileOpen`, protože nahrazujete úplně výchozí implementace rozhraní framework příkazu.  
  
-   Obslužná rutina použijte místo toho k zobrazení dialogového okna zdroje dat výpis. Můžete zobrazit dialogové okno voláním `CDatabase::OpenEx` nebo `CDatabase::Open` s parametrem **NULL**. Otevře se dialogové rozhraní ODBC, který se zobrazí všechny dostupné zdroje dat v počítači uživatele.  
  
-   Protože databázové aplikace obvykle není uložit celý dokument, budete pravděpodobně chtít odebrat uložení a uložit jako implementace, pokud nepoužíváte serializovaných dokument k ukládání informací o profilu. Jinak mohly implementovat příkazu Uložit jako, například "potvrzení transakce." V tématu [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md) pro další informace o přepsání těchto příkazů.  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Porovnání serializace a Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md)

