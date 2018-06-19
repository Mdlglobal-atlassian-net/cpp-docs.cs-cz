---
title: Atribut kontexty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e220eb0e7eb80d01d70aed82e773c46fe6704c7d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860330"
---
# <a name="attribute-contexts"></a>Kontexty atributů
Atributy C++ lze popsat pomocí čtyři základní pole: je možné použít pro cíl (**platí pro**), pokud jsou opakovatelných, nebo ne (**Repeatable**), vyžaduje přítomnost další atributy ( **Atributy požadované**) a nekompatibilitu s další atributy (**neplatné atributy**). Tato pole jsou uvedeny v doprovodné tabulce v tématu referenční každý atribut. Každá z těchto polí je popsána níže.  
  
## <a name="applies-to"></a>Platí pro  
 Toto pole popisuje různé prvky jazyka C++, které jsou právní cíle pro zadaný atribut. Například pokud atribut určuje "třída" v **platí pro** pole, to znamená, že atribut lze použít pouze právní třídy C++. Pokud atribut se použije k členské funkce třídy, výsledkem bude chyba syntaxe.  
  
 Další informace najdete v tématu [atributy podle použití](../windows/attributes-by-usage.md).  
  
## <a name="repeatable"></a>Opakovatelných  
 V tomto poli se zprávou, zda atribut můžete opakovaně použít pro stejný cíl. Většina atributy nejsou opakovatelných.  
  
## <a name="required-attributes"></a>Povinné atributy  
 Toto pole uvádí další atributy, které musí být přítomen (který se použije pro stejný cíl) pro zadaný atribut fungovat správně. Neobvyklé pro atribut, aby byly všechny položky v tomto poli.  
  
## <a name="invalid-attributes"></a>Neplatné atributy  
 Toto pole uvádí další atributy, které jsou kompatibilní se zadaným atributem. Neobvyklé pro atribut, aby byly všechny položky v tomto poli.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k atributům C++](../windows/cpp-attributes-reference.md)