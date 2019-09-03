---
title: alloc_text – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 7ddb12b39e068dea42f7a47f7fd937424be43725
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216335"
---
# <a name="alloc_text-pragma"></a>alloc_text – direktiva pragma

Pojmenuje oddíl kódu, do kterého mají být umístěny dané definice funkcí. Pro pojmenované funkce se tato direktiva pragma musí vyskytnout mezi deklarátorem funkce a její definicí.

## <a name="syntax"></a>Syntaxe

> **#pragma alloc_text (** "*textsection*" **;** *Function1* [ **;** *function2* ...] **)**

## <a name="remarks"></a>Poznámky

Direktiva pragma **alloc_text** nezpracovává C++ členské funkce ani přetížené funkce. Vztahuje se pouze na funkce deklarované s propojením jazyka C – to znamená funkce deklarované pomocí specifikace propojení **extern "C"** . Při pokusu o použití této direktivy pragma u funkce s propojením jazyka C++ dojde k vygenerování chyby kompilátoru.

Vzhledem k tomu, `__based` že funkce adresování pomocí není podporována, určení umístění oddílů vyžaduje použití direktivy pragma **alloc_text** . Název určený parametrem *textsection* by měl být uzavřený v uvozovkách.

Direktiva pragma **alloc_text** se musí vyskytovat za deklaracemi jakékoli ze zadaných funkcí a před definicemi těchto funkcí.

Funkce odkazované v direktivě pragma **alloc_text** by měly být definovány ve stejném modulu jako direktiva pragma. V opačném případě, pokud je nedefinovaná funkce později zkompilována do jiné části textu, chyba může nebo nemusí být zachycena. Ačkoli program bude obvykle fungovat správně, nebude funkce přidělena ve správném oddílu.

Další omezení pro **alloc_text** jsou následující:

- Nedá se použít uvnitř funkce.

- Musí být použita po deklaraci funkce, ale před její definicí.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
