---
title: Specifikátory a ekvivalenty datového typu
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
ms.openlocfilehash: 4003d9427c160b0e1c725cdc591190bd9777b3de
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151667"
---
# <a name="data-type-specifiers-and-equivalents"></a>Specifikátory a ekvivalenty datového typu

Tato kniha obecně namísto dlouhých tvarů používá tvary specifikátorů typů uvedené v následující tabulce a předpokládá, že typ `char` je ve výchozím nastavení se znaménkem. Proto je v této knize `char` je ekvivalentní **podepsané char**.

### <a name="type-specifiers-and-equivalents"></a>Specifikátory a ekvivalenty typu

|Specifikátor typu|Ekvivalenty|
|--------------------|---------------------|
|**podepsané char**1|**char**|
|**podepsané int**|**podepsané**, **int**|
|**krátká celočíselná podepsané**|**krátký**, **podepsané krátké**|
|**podepsané long int**|**dlouhé**, **podepsané dlouho**|
|**unsigned char**|—|
|**unsigned int**|**bez znaménka**|
|**unsigned short int**|**short bez znaménka**|
|**unsigned long int**|**unsigned long**|
|**float**|—|
|**long double**2|—|

1 je-li **char** typ bez znaménka ve výchozím nastavení (zadáním možnosti kompilátoru /), nelze zkrátit **podepsané char** jako **char**.

2 v 32bitových a 64bitových operačních systémech kompilátor Microsoft C mapuje **long double** na typ **double**.

**Microsoft Specific**

Můžete zadat možnost kompilátoru /J lze změnit výchozí **char** z typu se znaménkem na typ bez znaménka. Pokud tato možnost je ve skutečnosti **char** stejný význam jako **unsigned char**, a je nutné použít **podepsané** – klíčové slovo pro deklaraci hodnoty znaku se znaménkem. Pokud **char** hodnotu explicitně deklarována se znaménkem, možnost /J ji neovlivní a hodnota je rozšířen o znaménko při rozšíření na **int** typu. **Char** rozšířené při rozšíření na nula je typ **int** typu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Specifikátory typu jazyka C](../c-language/c-type-specifiers.md)
