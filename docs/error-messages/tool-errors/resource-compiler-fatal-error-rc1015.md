---
title: "Závažná chyba kompilátoru prostředků RC1015 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 666221cf5c3e812cd856271ea97cf4966383ec20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Závažná chyba kompilátoru prostředků RC1015
Nelze otevřít vložený soubor filename  
  
 Daný soubor neexistuje, nelze otevřít nebo nebyl nalezen.  
  
 Zajistěte, aby nastavení, prostředí musí být platný a zda je zadán správnou cestu k souboru. Zajistěte, aby dostatečná obslužných rutin souborů k dispozici pro kompilátor prostředků. Pokud je soubor na síťové jednotce, ujistěte se, zda máte oprávnění k otevření souboru.  
  
 RC1015 může dojít i v případě, že soubor existuje v adresáři, zadaný jako další zahrnout adresář ve vlastnostech konfigurace -> prostředků -> Stránka Obecné vlastnosti; Zadejte úplnou cestu k souboru zahrnout.  
  
 Další informace najdete v článku znalostní báze Knowledge Base Q326987: RC1015 chyby při použití prostředků zobrazení Pokud cesta zahrnutí je příliš dlouhý.