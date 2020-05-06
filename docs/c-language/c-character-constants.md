---
title: Konstanty znaků jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326297"
---
# <a name="c-character-constants"></a>Konstanty znaků jazyka C

"Znaková konstanta" je tvořena uzavřením jednoho znaku z množiny reprezentovatelné znakové sady v jednoduchých uvozovkách (**' '**). Znakové konstanty slouží k reprezentaci znaků ve [znakové sadě spuštění](../c-language/execution-character-set.md).

## <a name="syntax"></a>Syntaxe

*znaková konstanta*: **'** *c-char-Sequence* **'**

**L '** *c-char-Sequence* **'**

*c-char-Sequence*: *c-char*

*c-char-Sequence c-char*

*c-char*: libovolný člen zdrojové znakové sady s výjimkou jednoduché uvozovky (**'**), zpětného lomítka**\\**() nebo znaku nového řádku

*řídicí sekvence*

*sekvence escape*: *Jednoduchá řídicí* sekvence

*osmičková – řídicí sekvence*

*hexadecimální sekvence znaků*

*Jednoduchá řídicí sekvence*: jedna z **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*osmičková-řídicí sekvence*: **\\** *osmičková číslice*  

**\\**  *osmičková číslice osmičkové číslice*

**\\**  *osmičková číslice osmičkové číslice číslice*

*šestnáctkový řídicí znak sekvence*: **\x**  *hexadecimální číslice*

*šestnáctkové znaky-sekvence – hexadecimální číslice*

## <a name="see-also"></a>Viz také

[Konstanty jazyka C](../c-language/c-constants.md)
