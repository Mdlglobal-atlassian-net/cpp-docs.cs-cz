---
title: Specifikátory
ms.date: 11/04/2016
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
ms.openlocfilehash: aef967b26321f289cb8c7bd0402d7fe8f12b77b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330970"
---
# <a name="specifiers"></a>Specifikátory

Toto téma popisuje *specifikátory decl* součást (specifikátory deklarace) [deklarace](declarations-and-definitions-cpp.md).

Následující zástupné symboly a klíčová slova jazyka jsou specifikátory deklarace:

*storage-class-specifier*

*Specifikátor typu*

*Specifikátor funkce*

[friend](friend-cpp.md)

[typedef](aliases-and-typedefs-cpp.md) `(` *extended-decl-modifier-seq* `)`

[__declspec](declspec.md) `(` *extended-decl-modifier-seq* `)`

## <a name="remarks"></a>Poznámky

*Specifikátory decl* část deklarace je nejdelší sekvence *specifikátory decl* , dá se přenést do název typu bez zahrnutí ukazatel nebo odkaz na modifikátory. Zbývající část deklarace je *deklarátor*, který zahrnuje uvedený název.

V následující tabulce jsou uvedeny čtyři deklarace a pak zobrazí seznam jednotlivých deklarace *decl-specifers* a *deklarátor* komponenty samostatně.

|Deklarace|*specifikátory decl-*|`declarator`|
|-----------------|------------------------|------------------|
|`char *lpszAppName;`|**char**|`*lpszAppName`|
|`typedef char * LPSTR;`|**char**|`*LPSTR`|
|`const int func1();`|**Const int**|`func1`|
|`volatile void *pvvObj;`|**volatile void**|`*pvvObj`|

Protože **podepsané**, **bez znaménka**, **dlouhé**, a **krátký** všechny implikují **int**,  **Definice TypeDef** pojmenujte následující jedním z těchto klíčových slov za člena *seznam deklarátorů* není *specifikátory decl*.

> [!NOTE]
>  Vzhledem k tomu, že lze název předeklarovat, podléhá jeho interpretace poslední deklaraci v aktuálním rozsahu. Redeklarace může ovlivnit, jak jsou názvy interpretovány kompilátorem, zejména **typedef** názvy.

## <a name="see-also"></a>Viz také:

[Deklarace a definice](declarations-and-definitions-cpp.md)
