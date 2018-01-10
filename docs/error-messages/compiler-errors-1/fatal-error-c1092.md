---
title: "Závažná chyba C1092 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1092
dev_langs: C++
helpviewer_keywords: C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92309c9299303429c61f84911e180468f6354475
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1092"></a>Závažná chyba C1092
Upravit a pokračovat nepodporuje změny do datových typů; sestavení požadované  
  
 Změnit nebo přidat datový typ od poslední úspěšné sestavení.  
  
-   Upravit a pokračovat nepodporuje změny existujících datových typů, včetně definice třídy, struktury nebo výčtu. Musíte zastavit, ladění a sestavení aplikace.  
  
-   Upravit a pokračovat v přidání nové typy dat, pokud souboru databáze programu, například vc nepodporuje*x*0 pdb (kde *x* je hlavní verzi Visual C++ v použití) je jen pro čtení. Pokud chcete přidat datové typy, musí kompilátor otevřete soubor PDB v režimu zápisu.  
  
### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Chcete-li odebrat tuto chybu bez ukončení aktuální relaci ladění  
  
1.  Změna datového typu zpět do stavu před chyba.  
  
2.  Z **ladění** nabídce zvolte **použít změny kódu**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Chcete-li odebrat tuto chybu beze změny vašeho zdrojového kódu  
  
1.  Z **ladění** nabídce zvolte **Zastavte ladění**.  
  
2.  Z **sestavení** nabídce zvolte **sestavení**.  
  
 Další informace najdete v tématu [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).