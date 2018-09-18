---
title: Typ pro textové literály | Dokumentace Microsoftu
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
ms.openlocfilehash: 7773882d6fb04341a6f6d3a2cbcfda1d05f85d17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063278"
---
# <a name="type-for-string-literals"></a>Typ pro textové literály

Řetězcové literály obsahují pole typu `char` (to znamená **char [] č.**). (Řetězce širokého znaku mají pole typu `wchar_t` (to znamená **wchar_t [] č.**).) To znamená, že řetězec je pole s prvky typu `char`. Počet prvků v poli je roven počtu znaků v řetězci plus jeden pro ukončující znak null.

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)