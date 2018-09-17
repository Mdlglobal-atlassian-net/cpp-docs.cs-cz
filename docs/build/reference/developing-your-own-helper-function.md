---
title: Vývoj vlastní pomocné funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d95434c51bdfca07e48714c8c1e13bcdb64dc02f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715998"
---
# <a name="developing-your-own-helper-function"></a>Vývoj vlastní pomocné funkce

Můžete chtít poskytnout vlastní verzi rutiny na konkrétní zpracování na základě názvů imports nebo knihovny DLL. To provést dvěma způsoby: kódování vlastní, případně na základě zadaného kódu, nebo pouze připojení pomocí háky oznámení, které jsou podrobně popsané dříve poskytnutá verze.

## <a name="code-your-own"></a>Kód vlastní

To je poměrně jednoduché, protože je v podstatě použít zadaný kód jako vodítko pro nový uzel. Samozřejmě je potřeba dodržovat konvence volání a pokud vrátí převodní rutiny propojovacím programem, musí vracet ukazatele na správné funkci. Ve vašem kódu, jakmile provedete podstatě cokoli, co chcete, aby bylo možné splnit volání nebo využít volání.

## <a name="use-the-start-processing-notification-hook"></a>Spusťte zpracování oznámení háku

Bude pravděpodobně nejjednodušším stačí zadat nový ukazatel na funkci připojení uživatelem zadané oznámení, která přijímá stejné hodnoty jako výchozí pomocné rutiny na dliStartProcessing oznámení. V tomto okamžiku funkce háku se v podstatě stát novou funkci pomocné rutiny, jak úspěšně vrátit do pomocné rutiny výchozí obejde všechny další zpracování v pomocné výchozí.

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)