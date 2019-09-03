---
title: '#ifdef a #ifndef – direktivy (C/C++)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 433076388f3646b19d75a907c6b2254098096688
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220113"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>direktivy #ifdef a #ifndef (CC++/)

Direktivy **#ifdef** a **#ifndef** mají stejný účinek jako direktiva [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) , pokud se používá s definovaným operátorem.

## <a name="syntax"></a>Syntaxe

> **#ifdef** *identifikátor*\
> **#ifndef** *identifikátor*

Tyto direktivy jsou ekvivalentní:

> **#if definováno** *identifikátor*\
> **#if! definováno** *identifikátor*

## <a name="remarks"></a>Poznámky

Direktivy **#ifdef** a **#ifndef** můžete použít kdekoli `#if` . Příkaz **#ifdef** *identifikátor* je ekvivalentní, `#if 1` Pokud byl *identifikátor* definován. Je ekvivalentní s `#if 0` tím, že nebyl definován *identifikátor* nebo byl nedefinován `#undef` direktivou. Tyto direktivy kontrolují pouze přítomnost nebo absence identifikátorů definovaných pomocí `#define`, nikoli u identifikátorů deklarovaných ve zdrojovém kódu jazyka C nebo. C++

Tyto direktivy jsou k dispozici pouze pro kompatibilitu s předchozími verzemi jazyka. Upřednostňovaný výraz`#if` konstanty (identifikátor) použitý spolu s direktivou je upřednostňován.

Direktiva **#ifndef** kontroluje opak podmínky kontrolované **#ifdef**. Pokud identifikátor není definován nebo pokud byla jeho definice odebrána s `#undef`, je podmínka pravdivá (nenulová). V opačném případě je podmínka NEPRAVDA (0).

**Specifické pro společnost Microsoft**

*Identifikátor* lze předat z příkazového řádku pomocí možnosti [/d](../build/reference/d-preprocessor-definitions.md) . Pomocí `/D`lze zadat až 30 maker.

Direktiva **#ifdef** je užitečná pro kontrolu existence definice, protože definici lze předat z příkazového řádku. Příklad:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
