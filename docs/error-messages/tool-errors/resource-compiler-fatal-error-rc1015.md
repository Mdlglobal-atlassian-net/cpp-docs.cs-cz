---
title: Závažná chyba kompilátoru prostředků RC1015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7744242e44ecfc72ee57ab979969ad81b209e57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Závažná chyba kompilátoru prostředků RC1015
Nelze otevřít vložený soubor filename  
  
 Daný soubor neexistuje, nelze otevřít nebo nebyl nalezen.  
  
 Zajistěte, aby nastavení, prostředí musí být platný a zda je zadán správnou cestu k souboru. Zajistěte, aby dostatečná obslužných rutin souborů k dispozici pro kompilátor prostředků. Pokud je soubor na síťové jednotce, ujistěte se, zda máte oprávnění k otevření souboru.  
  
 RC1015 může dojít i v případě, že soubor existuje v adresáři, zadaný jako další zahrnout adresář ve vlastnostech konfigurace -> prostředků -> Stránka Obecné vlastnosti; Zadejte úplnou cestu k souboru zahrnout.  
  
 Další informace najdete v článku znalostní báze Knowledge Base Q326987: RC1015 chyby při použití prostředků zobrazení Pokud cesta zahrnutí je příliš dlouhý.