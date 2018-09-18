---
title: Převody z podepsaných integrálních typů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fc38fd8b1ab4bc84898704218b2da5722514cea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101381"
---
# <a name="conversions-from-signed-integral-types"></a>Převody z podepsaných integrálních typů

Když celé číslo se znaménkem je převést na celé číslo bez znaménka s roven nebo větší velikostí, hodnota celé číslo se znaménkem není záporná hodnota se nezmění. Převod je proveden tím, že znak rozšíří celé číslo se znaménkem. Celé číslo se znaménkem je převést na kratší celé číslo se znaménkem zkrácením nejvyšších bitů. Výsledkem je interpretován jako hodnoty bez znaménka, jak je znázorněno v tomto příkladu.

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Žádné informace jsou ztraceny, pokud celé číslo se znaménkem je převedena na hodnotu s plovoucí desetinnou čárkou s tím rozdílem, že mohou být ztraceny některé přesnosti, když **long int** nebo **unsigned long int** hodnota je převedena na **float** hodnotu.

Následující tabulka shrnuje převody z podepsaných integrálních typů. Tato tabulka předpokládá, že **char** ve výchozím nastavení je typ podepsaný. Chcete-li změnit výchozí nastavení pro možnost kompilace použijete **char** typ bez znaménka, převody uvedené v [převody z nepodepsaných integrálních typů](../c-language/conversions-from-unsigned-integral-types.md) tabulky pro **unsigned char**  typ použít namísto převody v následující tabulce, převody z celočíselných typů se znaménkem.

### <a name="conversions-from-signed-integral-types"></a>Převody z podepsaných integrálních typů

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**Char**1|**short**|Znak rozšíření|
|**char**|**long**|Znak rozšíření|
|**char**|**unsigned char**|Zachovat vzor; bit vyššího řádu jako bit znaménka ztratí – funkce|
|**char**|**short bez znaménka**|Rozšíření přihlašování do **krátký**; převod **krátký** k **unsigned short**|
|**char**|**unsigned long**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **unsigned long**|
|**char**|**float**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **plovoucí desetinnou čárkou**|
|**char**|**double**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **double**|
|**char**|**typ long double**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **double**|
|**short**|**char**|Zachovat dolní bajty.|
|**short**|**long**|Znak rozšíření|
|**short**|**unsigned char**|Zachovat dolní bajty.|
|**short**|**short bez znaménka**|Zachovat bitový vzor; bit vyššího řádu jako bit znaménka ztratí – funkce|
|**short**|**unsigned long**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **unsigned long**|
|**short**|**float**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **plovoucí desetinnou čárkou**|
|**short**|**double**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **double**|
|**short**|**typ long double**|Rozšíření přihlašování do **dlouhé**; převést **dlouhé** k **double**|
|**long**|**char**|Zachovat dolní bajty.|
|**long**|**short**|Zachovat nižší řád slova|
|**long**|**unsigned char**|Zachovat dolní bajty.|
|**long**|**short bez znaménka**|Zachovat nižší řád slova|
|**long**|**unsigned long**|Zachovat bitový vzor; bit vyššího řádu jako bit znaménka ztratí – funkce|
|**long**|**float**|Znázornění jako **float**. Pokud **dlouhé** se nedá přesně prezentovat některé je ztráta přesnosti.|
|**long**|**double**|Znázornění jako **double**. Pokud **dlouhé** nemůže být reprezentován přesně jako **double**, dojde ke ztrátě některých přesnosti.|
|**long**|**typ long double**|Znázornění jako **double**. Pokud **dlouhé** nemůže být reprezentován přesně jako **double**, dojde ke ztrátě některých přesnosti.|

1. Všechny **char** položky se předpokládá, že **char** ve výchozím nastavení je typ podepsaný.

**Specifické pro Microsoft**

Pro kompilátor jazyka C společnosti Microsoft 32-bit integer je ekvivalentní **dlouhé**. Převod **int** hodnotu pokračuje stejné jako v případě **dlouhé**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)