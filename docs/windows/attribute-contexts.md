---
title: Atribut kontexty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e3935b168220b528afaecd2e1438cfe49496b1b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313660"
---
# <a name="attribute-contexts"></a>Kontexty atributů
Atributy C++ lze popsat pomocí čtyři základní pole: cíl se můžou uplatnit na (**platí pro**), pokud jsou opakovatelné nebo ne (**Repeatable**), vyžaduje přítomnost dalších atributů ( **Atributy požadované**) a nekompatibilitu s další atributy (**neplatné atributy**). Tato pole jsou uvedeny v související tabulce v tématu referenční každý atribut. Každá z těchto polí je popsána níže.
  
## <a name="applies-to"></a>Platí pro
 Toto pole popisuje různé prvky jazyka C++, které jsou platné cíle pro zadaného atributu. Například pokud atribut určuje "třída" v **platí pro** pole, to znamená, že atribut lze použít pouze na právní třídu C++. Pokud je atribut použit na členskou funkci třídy, výsledkem bude chyba syntaxe.
  
 Další informace najdete v tématu [atributy podle použití](../windows/attributes-by-usage.md).
  
## <a name="repeatable"></a>Opakovatelné
 Toto pole je uvedeno, zda je atribut pro stejný cíl opakovaně použít. Většina atributy nejsou opakovatelné.
  
## <a name="required-attributes"></a>Vyžadované atributy
 Toto pole obsahuje další atributy, které musí být přítomná (který se použije pro stejný cíl) pro zadaný atribut fungovat správně. Je běžné pro atribut, který má obsahovat žádné položky pro toto pole.
  
## <a name="invalid-attributes"></a>Neplatné atributy
 Toto pole obsahuje další atributy, které nejsou kompatibilní se zadaným atributem. Je běžné pro atribut, který má obsahovat žádné položky pro toto pole.
  
## <a name="see-also"></a>Viz také
 [Referenční dokumentace k atributům C++](../windows/cpp-attributes-reference.md)