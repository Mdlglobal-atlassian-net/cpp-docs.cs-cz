---
title: '#undef – direktiva (C/C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#undef'
dev_langs:
- C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16b8c937ad62ddc6738c626543dab2d4e5453bc5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839777"
---
# <a name="undef-directive-cc"></a>#undef – direktiva (C++)
Odebere (zruší definici) název dříve vytvořený pomocí direktivy `#define`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#undef   
identifier  
  
```  
  
## <a name="remarks"></a>Poznámky  
 `#undef` – Direktiva odebere aktuální definice *identifikátor*. V důsledku toho následné výskyty *identifikátor* preprocesor ignoruje. Chcete-li odebrat pomocí definice – makro `#undef`, zadejte pouze makra *identifikátor* ; neudělujte seznam parametrů.  
  
 Pro identifikátor, který nemá žádnou předchozí definici, lze také použít direktivu `#undef`. Tím je zajištěno, že tento identifikátor není definován. Nahrazení makra není v rámci příkazů `#undef` prováděno.  
  
 Direktiva `#undef` je obvykle spojená s direktivou `#define`, což vytvoří ve zdrojovém programu oblast, ve které má identifikátor zvláštní význam. Určitá funkce zdrojového programu například může použít konstanty manifestu pro definování hodnot specifických pro prostředí, které nemají vliv na zbytek programu. Direktiva `#undef` také funguje s direktivou `#if` pro řízení podmíněné kompilace zdrojového programu. V tématu [#if, #elif, #else a #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) Další informace.  
  
 V následujícím příkladu odebere direktiva `#undef` definice symbolické konstanty a makra. Je uveden pouze identifikátor makra.  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Konkrétní Microsoft**  
  
 Z příkazového řádku lze zrušit definici maker pomocí možnosti /U následované názvy maker, jejichž definice mají být zrušeny. Účinek zadáním tohoto příkazu je ekvivalentní posloupnost `#undef` *název makra* příkazy na začátku souboru.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)