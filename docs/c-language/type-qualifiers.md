---
title: Zadejte kvalifikátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc0fd45887975c9b50cee141b0c6e8faca33513
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083240"
---
# <a name="type-qualifiers"></a>Kvalifikátory typu

Kvalifikátory typu poskytnout jednu ze dvou vlastností na identifikátor rozhraní. **Const** kvalifikátor typu deklaruje objekt bude neupravitelnými. `volatile` Kvalifikátor typu deklaruje položku, jehož hodnota může oprávněně změnit něco mimo ovládací prvek programu, ve kterém se zobrazí, jako je například souběžně prováděným vláknem.

Kvalifikátory, zadejte dva **const** a `volatile`, může být použito pouze jednou v deklaraci. Kvalifikátory typu se může zobrazit všechny specifikátorem typu; však nemůže objevit po první čárku v deklaraci více položek. Například následující deklarace jsou platné:

```
typedef volatile int VI;
const int ci;
```

Nejsou povoleny tyto deklarace:

```
typedef int *i, volatile *vi;
float f, const cf;
```

Kvalifikátory typu jsou relevantní pouze v případě, že přístup k identifikátory jako l hodnoty ve výrazech. Zobrazit [výrazy L-Value a R-Value](../c-language/l-value-and-r-value-expressions.md) informace o l hodnoty a výrazy.

## <a name="syntax"></a>Syntaxe

*Kvalifikátor typu*: **constvolatile**

Následující jsou přípustné **const** a `volatile` deklarace:

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

Pokud specifikace typu pole obsahuje kvalifikátory typu, je kvalifikován elementu, není typu pole. Pokud specifikace typu funkce obsahuje kvalifikátory, není chování definováno. Ani `volatile` ani **const** má vliv na rozsah hodnot nebo aritmetické vlastností objektu.

Tento seznam popisuje způsob použití **const** a `volatile`.

- **Const** – klíčové slovo lze použít k úpravě jakékoli základní nebo agregační typ nebo ukazatel na objekt typu, nebo `typedef`. Pokud položka je deklarována s pouze **const** kvalifikátor typu, jeho typ slov za **const int**. A **const** lze inicializovat proměnnou nebo mohou být umístěny v oblasti úložiště, jen pro čtení. **Const** – klíčové slovo je užitečné k deklaraci ukazatele na **const** vzhledem k tomu, že to vyžaduje funkce nebudou je moci měnit ukazatel žádným způsobem.

- Kompilátor předpokládá, že, kdekoli v programu, `volatile` proměnná je možný přes neznámý proces, který používá nebo upravuje jeho hodnotu. Proto, bez ohledu na to, na příkaz určených optimalizacích řádek kódu pro každé přiřazení nebo odkaz na `volatile` proměnnou je nutné vygenerovat i v případě, že se zobrazuje v nemají žádný vliv.

   Pokud `volatile` použitý samostatně, `int` se předpokládá, že. `volatile` Specifikátor typu je možné poskytovat spolehlivý přístup k umístění v paměti speciální. Použití `volatile` s datové objekty, které může získat přístup nebo upravené pomocí obslužné rutiny signálu souběžně prováděných programů nebo speciální hardware jako mapované paměti zaregistruje řízení vstupně-výstupních operací. Je možné deklarovat jako proměnnou `volatile` pro svého životního cyklu, nebo můžete přetypovat jeden odkaz bude `volatile`.

- Položka může být obojí **const** a `volatile`, v takovém případě položky nelze je změnit oprávněně vlastní program, ale může změnit některé asynchronní proces.

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)