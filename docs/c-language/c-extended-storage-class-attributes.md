---
title: Rozšířené atributy třídy úložiště jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: c2e372ebe93b9240ac6f489e8b1aefc1fbbded80
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857148"
---
# <a name="c-extended-storage-class-attributes"></a>Rozšířené atributy třídy úložiště jazyka C

**Specifické pro Microsoft**

Další informace o tomto tématu najdete v části [__declspec (Referenční dokumentace jazyka C++)](../cpp/declspec.md).

Rozšířená syntaxe atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyka C. Mezi atributy třídy úložiště používající rozšířenou syntaxi atributů patří atributy thread, naked, dllimport a dllexport.

Rozšířená syntaxe atributů pro určení informací o třídě úložiště používá klíčové slovo __declspec, které určuje, že se instance daného typu uloží do níže uvedeného atributu třídy úložiště specifické pro společnost Microsoft (thread, naked, dllimport nebo dllexport). Příklady dalších modifikátorů tříd úložišť mohou být klíčová slova static a extern. Tato klíčová slova jsou však součástí standardu ANSI C a jako taková nejsou součástí rozšířené syntaxe atributů.

## <a name="syntax"></a>Syntaxe

*specifikátor třídy úložiště*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *Rozšířené prohlášení-modifikátor-SEQ* **)**  / \* specifické pro společnost Microsoft\*/

*Extended---modifikátor-SEQ*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Rozšířené-prohlášení – modifikátor*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended---modifikátor-SEQ* *Extended---modifikátor*

*Rozšířené – modifikátor*&nbsp; &nbsp; &nbsp; &nbsp; :/ specifické\* pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Doporučujeme**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**okem**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**atributu**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

Modifikátory deklarace jsou odděleny prázdným znakem. Všimněte si, že *příkaz Extended---modifikátor-SEQ* může být prázdný. v takovém případě nemá __declspec žádný vliv.

Atributy třídy úložiště thread, naked, dllimport a dllexport jsou vlastnostmi pouze té deklarace dat nebo funkce, pro kterou jsou použity. Tyto atributy nemění definice atributů typů samotné funkce. Atribut thread ovlivňuje pouze data. Atribut naked ovlivňuje pouze funkce. Atributy dllimport a dllexport ovlivňují funkce i data.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
