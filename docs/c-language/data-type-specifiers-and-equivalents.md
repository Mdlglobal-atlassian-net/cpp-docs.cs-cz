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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234927"
---
# <a name="data-type-specifiers-and-equivalents"></a>Specifikátory a ekvivalenty datového typu

Tato kniha obecně namísto dlouhých tvarů používá tvary specifikátorů typů uvedené v následující tabulce a předpokládá, že typ `char` je ve výchozím nastavení se znaménkem. Proto `char` je v celé této příručce ekvivalentem **podepsaného znaku**.

### <a name="type-specifiers-and-equivalents"></a>Specifikátory a ekvivalenty typu

|Specifikátor typu|Ekvivalenty|
|--------------------|---------------------|
|**signed char**1|**char**|
|**celé číslo se znaménkem**|**signed**, **int**|
|**krátké celé číslo se znaménkem**|**short**, **signed short**|
|**celé číslo se znaménkem long int**|**Long**, **podepsaná Long**|
|**unsigned char**|—|
|**unsigned int**|**celé**|
|**krátké celé číslo bez znaménka**|**unsigned short**|
|**dlouhé celé číslo bez znaménka**|**unsigned long**|
|**Plovák**|—|
|**dlouhé Double**2|—|

1 když ve výchozím nastavení nastavíte typ **znaku** bez znaménka (zadáním možnosti kompilátoru/j), nemůžete **podepsat znak typu signed** jako **char**.

2 v 32 a 64 bitových operačních systémů, kompilátor jazyka Microsoft C mapuje **Long Double** na typ **Double**.

**Specifické pro Microsoft**

Můžete zadat možnost kompilátoru/J pro změnu výchozího typu **char** z signed na unsigned. Je-li tato možnost platná, **znak** znamená stejný jako **nepodepsaný znak**a je nutné použít klíčové slovo **signed** pro deklaraci podepsaného znaku. Pokud je hodnota **znaku** explicitně deklarována jako podepsaná, možnost/j to nijak neovlivní a hodnota je znaménko při rozšíření na typ **int** . Typ **znaku** je po rozšíření na typ **int** rozšířený na nulu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Specifikátory typu jazyka C](../c-language/c-type-specifiers.md)
