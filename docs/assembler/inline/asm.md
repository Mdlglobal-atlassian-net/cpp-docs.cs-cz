---
title: __asm | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- __asm
- _asm
- __asm_cpp
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd279a6324aec6eba50c6c3b7ffe846200d45fe1
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161720"
---
# <a name="asm"></a>__asm

**Specifické pro Microsoft**

`__asm` – Klíčové slovo vyvolá vložený assembler a může se objevit všude, kde je platný příkaz jazyka C nebo C++. Se nemůže objevit samostatně. Musí následovat instrukce sestavení, skupina pokynů uzavřená v závorkách, nebo přinejmenším, prázdný pár závorek. Termín "`__asm` blok" zde vztahuje na jakoukoli instrukci nebo skupinu instrukcí ve složených závorkách, zda je či není.

> [!NOTE]
> Podpora Visual C++ jazyka Standard C++ `asm` – klíčové slovo je omezena na skutečnost, že kompilátor nevygeneruje chybu pro klíčové slovo. Nicméně `asm` bloku se nevygeneruje jakýkoli smysluplný kód. Použití `__asm` místo `asm`.

## <a name="grammar"></a>Gramatika

*asm bloku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm** *instrukci sestavení* **;** <sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {** *sestavení seznam instrukcí-* **}** **;** <sub>optimalizované</sub>

*sestavení seznam instrukcí-*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukci sestavení* **;** <sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukci sestavení* **;** *sestavení seznam instrukcí-* **;** <sub>optimalizované</sub>

## <a name="remarks"></a>Poznámky

Je-li použito bez závorek, `__asm` – klíčové slovo znamená, že zbytek řádku je příkaz jazyka sestavení. Pokud používáno se závorkami, znamená to, že každý řádek mezi závorkami je příkaz jazyka sestavení. Z důvodu kompatibility s předchozími verzemi `_asm` je synonymum pro `__asm`.

Vzhledem k tomu, `__asm` – klíčové slovo představuje oddělovač, můžete umístit pokyny sestavení na stejném řádku.

Před Visual C++ 2005, instrukce

```cpp
__asm int 3
```

nezpůsobil nativního kódu při kompilaci s vygenerování **/CLR**; kompilátor přeložil pokyn k instrukci CLR break.

`__asm int 3` nyní způsobí generování nativního kódu pro funkci. Pokud chcete, aby funkce způsobila přerušení v kódu a pokud chcete tuto funkci zkompilovat pro jazyk MSIL, použijte [__debugbreak](../../intrinsics/debugbreak.md).

Z důvodu kompatibility s předchozími verzemi **_asm** je synonymum pro **__asm** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../../build/reference/za-ze-disable-language-extensions.md) určena.

## <a name="example"></a>Příklad

Následující fragment kódu je jednoduchý `__asm` bloku, které jsou uzavřeny ve složených závorkách:

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Alternativně můžete umístit `__asm` před každou instrukci sestavení:

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Vzhledem k tomu, `__asm` – klíčové slovo představuje oddělovač, můžete také umístit pokyny sestavení na stejný řádek:

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Všechny tři příklady vygenerují stejný kód, ale první styl (uzavírající `__asm` blokovat ve složených závorkách) má několik výhod. Složené závorky jasně oddělují kód sestavení od kódu jazyka C nebo C++ a vyhnout se zbytečnému opakování `__asm` – klíčové slovo. Složené závorky také zabraňují nejasnostem. Pokud chcete umístit příkaz C nebo C++ na stejném řádku jako `__asm` bloku, blok je nutné uzavřít do složených závorek. Bez závorek kompilátor nemůže určit, kde zastaví sestavení kódu a příkazy jazyka C nebo C++ začít. A konečně protože text v závorce má stejný formát jako obyčejný text MASM, můžete snadno vyjmout a vložit text z existujících zdrojových souborů MASM.

Na rozdíl od složených závorek v jazyce C a C++, složené závorky uzavírající `__asm` bloku nemají vliv na rozsah proměnné. Lze také vnořit `__asm` bloky; vnoření nemá vliv na rozsah proměnné.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../../cpp/keywords-cpp.md)<br/>
[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>