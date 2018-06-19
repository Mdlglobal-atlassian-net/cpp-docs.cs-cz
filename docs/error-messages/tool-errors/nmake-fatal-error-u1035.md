---
title: Závažná chyba nástroje NMAKE U1035 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb32f815345b933ad6a65a0c8c1ec8ad59cbe81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322793"
---
# <a name="nmake-fatal-error-u1035"></a>Závažná chyba nástroje NMAKE U1035
Chyba syntaxe: očekáváno ':' nebo '=' oddělovač  
  
 Buď dvojtečkou (**:**) nebo symbol rovná (**=**) byl očekáván.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Dvojtečkou nesledovala cíl.  
  
2.  Dvojtečkou a žádné místo (například a:) a cíl jedním písmenem. NMAKE ji interpretovat jako určení jednotky.  
  
3.  Dvojtečkou nesledovala odvozené pravidlo.  
  
4.  Symbol rovná nenásledovala definici makra.  
  
5.  Znak, a potom zpětné lomítko (**\\**), který byl použit pokračujte příkazu, který bude nový řádek.  
  
6.  Řetězec zobrazovaly který nesledovala žádné pravidlo NMAKE syntaxe.  
  
7.  Souboru pravidel byl formátován pomocí textový editor.