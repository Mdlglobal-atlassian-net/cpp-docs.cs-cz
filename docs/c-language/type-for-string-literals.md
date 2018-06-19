---
title: Typ pro textové literály | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bfabc412c46a5fa73bf0cd3d000bb3823e5a389
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386768"
---
# <a name="type-for-string-literals"></a>Typ pro textové literály
Textové literály mít typ pole `char` (tedy **char []**). (Široká charakterová řetězce mít typ pole `wchar_t` (tedy **[] wchar_t**).) To znamená, že řetězec je pole s prvky typu `char`. Počet prvků v poli je roven počtu znaků v řetězci plus jeden pro ukončující znak null.  
  
## <a name="see-also"></a>Viz také  
 [Textové literály jazyka C](../c-language/c-string-literals.md)