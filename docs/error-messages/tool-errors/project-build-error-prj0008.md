---
title: Chyba sestavení projektu PRJ0008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4011a27b7e6707f9c9b4e3ed386306b00f2792cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317642"
---
# <a name="project-build-error-prj0008"></a>Chyba sestavení projektu PRJ0008
Soubor 'file' se nepodařilo odstranit.  
  
 **Ujistěte se, zda soubor není otevřen jiným procesem a není chráněna proti zápisu.**  
  
 Při opětovném sestavení nebo vyčistit, Visual C++ odstraní všechny známé zprostředkující a výstupní soubory pro sestavení, a také všechny soubory, které splňují specifikace zástupného znaku v **rozšíření k odstranění na vyčištění** vlastnost [obecné Stránka vlastností nastavení konfigurace](../../ide/general-property-page-project.md).  
  
 Tato chyba se zobrazí, pokud není možné odstranit soubor Visual C++. Chcete-li vyřešit chyby, ujistěte se, souboru a jeho adresáře nelze zapisovat pro uživatele provádějícího sestavení.