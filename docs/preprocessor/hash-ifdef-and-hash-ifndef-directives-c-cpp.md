---
title: '#ifdef a #ifndef direktivy (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 418b19e844d56fa2f33cf91a1b072e9add771eb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643791"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef a #ifndef – direktivy (C/C++)
**#Ifdef** a **#ifndef** direktivy provádějí stejné úkoly, jako `#if` směrnice, i když se použije s parametrem **definované**( *identifikátor* ).

## <a name="syntax"></a>Syntaxe

```
#ifdef identifier
#ifndef identifier

// equivalent to
#if defined identifier
#if !defined identifier
```

## <a name="remarks"></a>Poznámky

Můžete použít **#ifdef** a **#ifndef** direktivy kdekoli `#if` lze použít. **#Ifdef** *identifikátor* je ekvivalentní příkazu `#if 1` při *identifikátor* byla definována, a je ekvivalentní `#if 0` při *identifikátor* nebyla definována nebo byla jeho definice zrušena pomocí `#undef` směrnice. Tyto směrnice zkontrolují pouze přítomnost nebo nepřítomnost identifikátorů definovaných pomocí `#define`, nikoli identifikátorů, které jsou deklarovány ve zdrojovém kódu jazyka C nebo C++.

Tyto směrnice jsou poskytovány pouze pro kompatibilitu s předchozími verzemi jazyka. **Definované (** *identifikátor* **)** konstantním výrazu použitém s `#if` – direktiva je upřednostňována.

**#Ifndef** směrnice hledá opak podmínky ověřované direktivou **#ifdef**. Pokud nebyl definován identifikátor (nebo byla odebrána jeho definice s `#undef`), podmínka je PRAVDA (nenulové). V opačném případě je podmínka NEPRAVDA (0).

**Specifické pro Microsoft**

*Identifikátor* lze předávat z příkazového řádku pomocí `/D` možnost. Až 30 maker je možné zadat při `/D`.

To je užitečné pro kontrolu, jestli existuje definice, protože definice může být předána z příkazového řádku. Příklad:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)