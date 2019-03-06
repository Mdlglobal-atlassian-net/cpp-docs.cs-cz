---
title: Vývoj vlastní pomocné funkce
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: 2601aff6b53e9ad3a970dbe1be008efdd7008ef8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424428"
---
# <a name="developing-your-own-helper-function"></a>Vývoj vlastní pomocné funkce

Můžete chtít poskytnout vlastní verzi rutiny na konkrétní zpracování na základě názvů imports nebo knihovny DLL. To provést dvěma způsoby: kódování vlastní, případně na základě zadaného kódu, nebo pouze připojení pomocí háky oznámení, které jsou podrobně popsané dříve poskytnutá verze.

## <a name="code-your-own"></a>Kód vlastní

To je poměrně jednoduché, protože je v podstatě použít zadaný kód jako vodítko pro nový uzel. Samozřejmě je potřeba dodržovat konvence volání a pokud vrátí převodní rutiny propojovacím programem, musí vracet ukazatele na správné funkci. Ve vašem kódu, jakmile provedete podstatě cokoli, co chcete, aby bylo možné splnit volání nebo využít volání.

## <a name="use-the-start-processing-notification-hook"></a>Spusťte zpracování oznámení háku

Bude pravděpodobně nejjednodušším stačí zadat nový ukazatel na funkci připojení uživatelem zadané oznámení, která přijímá stejné hodnoty jako výchozí pomocné rutiny na dliStartProcessing oznámení. V tomto okamžiku funkce háku se v podstatě stát novou funkci pomocné rutiny, jak úspěšně vrátit do pomocné rutiny výchozí obejde všechny další zpracování v pomocné výchozí.

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)
