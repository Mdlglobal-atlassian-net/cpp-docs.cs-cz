---
title: Rozšířené atributy třídy úložiště jazyka C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fd89e21b10d241ea035e8c9b9c8ac8e5c3ee9cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106076"
---
# <a name="c-extended-storage-class-attributes"></a>Rozšířené atributy třídy úložiště jazyka C

**Specifické pro Microsoft**

Více aktuální informace o tomto tématu najdete v části [__declspec (referenční dokumentace jazyka C++)](../cpp/declspec.md).

Rozšířená syntaxe atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyka C. Mezi atributy třídy úložiště používající rozšířenou syntaxi atributů patří atributy thread, naked, dllimport a dllexport.

Rozšířená syntaxe atributů pro určení informací o třídě úložiště používá klíčové slovo __declspec, které určuje, že se instance daného typu uloží do níže uvedeného atributu třídy úložiště specifické pro společnost Microsoft (thread, naked, dllimport nebo dllexport). Příklady dalších modifikátorů tříd úložišť mohou být klíčová slova static a extern. Tato klíčová slova jsou však součástí standardu ANSI C a jako taková nejsou součástí rozšířené syntaxe atributů.

## <a name="syntax"></a>Syntaxe

*Storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl-modifier-seq* **)**  / \* specifické pro Microsoft \*/

*Extended-decl-modifier-seq*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl modifikátor*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier-seq* *extended-decl – modifikátor*

*Extended-decl modifikátor*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vlákno**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

Modifikátory deklarace jsou odděleny prázdným znakem. Všimněte si, že *extended-decl-modifier-seq* může být prázdný; v takovém případě nemá atribut __declspec žádný vliv.

Atributy třídy úložiště thread, naked, dllimport a dllexport jsou vlastnostmi pouze té deklarace dat nebo funkce, pro kterou jsou použity. Tyto atributy nemění definice atributů typů samotné funkce. Atribut thread ovlivňuje pouze data. Atribut naked ovlivňuje pouze funkce. Atributy dllimport a dllexport ovlivňují funkce i data.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)