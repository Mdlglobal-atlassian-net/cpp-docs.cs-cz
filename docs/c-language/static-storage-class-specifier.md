---
title: statický specifikátor třídy úložiště | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1a58a8c7ab6eeb7d304d84cef15beb9046184fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079489"
---
# <a name="static-storage-class-specifier"></a>Statický specifikátor třídy úložiště

Proměnná deklarovaná na vnitřní úrovni **statické** – specifikátor třídy úložiště má globální dobu platnosti, ale je viditelný pouze v rámci bloku ve kterém je deklarována. Pro konstantní řetězce je použití **statické** je užitečné, protože zmírňuje režii časté inicializace v často volaných funkcích.

## <a name="remarks"></a>Poznámky

Pokud neinicializujete explicitně **statické** proměnné, je inicializován na 0 ve výchozím nastavení. Uvnitř funkce **statické** způsobí, že je přiděleno úložiště a slouží jako definice. Vnitřní statické proměnné poskytují trvalé soukromé úložiště, které je viditelné pouze jedinou funkcí.

## <a name="see-also"></a>Viz také

[Třídy úložiště jazyka C](c-storage-classes.md)<br/>
[Třídy úložiště (C++)](../cpp/storage-classes-cpp.md)