---
title: Volání s proměnlivým počtem argumentů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipses (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec70da7259ce0b04334bf9c0e1f529e76b46c6c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028217"
---
# <a name="calls-with-a-variable-number-of-arguments"></a>Volání s proměnlivým počtem argumentů

Částečný seznam parametrů lze ukončit zápisem tří teček, čárkou následovanou třemi tečkami (**;...** ), k označení, že mohou být další argumenty předané funkci, ale žádné další informace o nich zadány. Na těchto argumentech se neprovádí kontrola typu. Zápis tří teček musí předcházet alespoň jeden parametr a tento zápis tří teček musí být posledním tokenem v seznamu parametrů. Bez zápisu tří teček není chování funkce definováno, pokud obdrží jiné parametry než ty deklarované v seznamu parametrů.

Chcete-li funkci zavolat s proměnným počtem argumentů, stačí ve volání funkce zadat libovolný počet argumentů. Příkladem je funkce `printf` z knihovny modulu runtime jazyka C. Volání funkce musí obsahovat jeden argument pro každý název typu, který je deklarován v seznamu parametrů nebo v seznamu typů argumentů.

Všechny argumenty zadané ve volání funkce jsou umístěny na zásobník, pokud není zadána konvence volání `__fastcall`. Počet parametrů deklarovaných pro funkci určuje, kolik argumentů je odebráno ze zásobníku a přiřazeno parametrům. Jste zodpovědní za načtení jakýchkoli dalších argumentů ze zásobníku a za určení počtu přítomných argumentů. Soubor STDARG.H obsahuje makra ve stylu standardu ANSI pro přístup k argumentům funkce, která přijímá proměnný počet argumentů. Také jsou stále podporována makra ve stylu XENIX v souboru VARARGS.H.

Tato ukázka deklarace je funkcí, kterou lze volat s proměnným počtem argumentů:

```
int average( int first, ...);
```

## <a name="see-also"></a>Viz také

[Volání funkcí](../c-language/function-calls.md)