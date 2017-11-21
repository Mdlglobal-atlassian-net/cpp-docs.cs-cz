---
title: "Chyba sestavení projektu PRJ0008 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0008
dev_langs: C++
helpviewer_keywords: PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41410c2ddecd6798a994114a70192441abe675a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0008"></a>Chyba sestavení projektu PRJ0008
Soubor 'file' se nepodařilo odstranit.  
  
 **Ujistěte se, zda soubor není otevřen jiným procesem a není chráněna proti zápisu.**  
  
 Při opětovném sestavení nebo vyčistit, Visual C++ odstraní všechny známé zprostředkující a výstupní soubory pro sestavení, a také všechny soubory, které splňují specifikace zástupného znaku v **rozšíření k odstranění na vyčištění** vlastnost [obecné Stránka vlastností nastavení konfigurace](../../ide/general-property-page-project.md).  
  
 Tato chyba se zobrazí, pokud není možné odstranit soubor Visual C++. Chcete-li vyřešit chyby, ujistěte se, souboru a jeho adresáře nelze zapisovat pro uživatele provádějícího sestavení.