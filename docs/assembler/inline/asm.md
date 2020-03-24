---
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: de28e4c0fad6b89a62b4479c5c32f0b8606cf3af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169628"
---
# <a name="__asm"></a>__asm

**Specifické pro společnost Microsoft**

Klíčové slovo `__asm` vyvolá vložený assembler a může se objevit všude, kde je výraz C++ C nebo platný. Nemůže být použit sám sebou. Musí následovat instrukce sestavení, skupina instrukcí uzavřených ve složených závorkách nebo, minimálně prázdný pár složených závorek. Termín "`__asm` blok" tady odkazuje na jakoukoli instrukci nebo skupinu instrukcí, bez ohledu na to, jestli jsou ve složených závorkách.

> [!NOTE]
> Podpora C++ vizuálů pro klíčové slovo C++ Standard `asm` je omezena na skutečnost, že kompilátor nevygeneruje chybu pro klíčové slovo. Nicméně blok `asm` nebude generovat žádný smysluplný kód. Místo `asm`použijte `__asm`.

## <a name="grammar"></a>Gramatika

*ASM – blok*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm** *sestavení-instrukce* **;** <sub>výslovný souhlas</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *Assembly-Instruction-list* **}** **;** <sub>výslovný souhlas</sub>

*seznam instrukcí pro sestavení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sestavení-instrukce* **;** <sub>výslovný souhlas</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sestavení-instrukce* **;** *Assembly-instrukces-list* **;** <sub>výslovný souhlas</sub>

## <a name="remarks"></a>Poznámky

Pokud se používá bez složených závorek, klíčové slovo `__asm` znamená, že zbytek řádku je příkaz Assembly-Language. Pokud se používá se složenými závorkami, znamená to, že každý řádek mezi složenými závorkami je příkaz Assembly-Language. Pro zajištění kompatibility s předchozími verzemi je `_asm` synonymem pro `__asm`.

Vzhledem k tomu, že klíčové slovo `__asm` je oddělovač příkazů, lze umístit pokyny sestavení na stejný řádek.

Před Visual Studio 2005, instrukce

```cpp
__asm int 3
```

nezpůsobí generování nativního kódu při kompilování s **/CLR**; Kompilátor přeložil instrukci na instrukci ukončení CLR.

`__asm int 3` nyní má za následek generování nativního kódu pro funkci. Chcete-li, aby funkce způsobila v kódu bod přerušení, a pokud chcete tuto funkci zkompilovat do jazyka MSIL, použijte [__debugbreak](../../intrinsics/debugbreak.md).

Z důvodu kompatibility s předchozími verzemi je **_asm** synonymem pro **__asm** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Příklad

Následující fragment kódu je jednoduchý blok `__asm` uzavřený ve složených závorkách:

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

Protože klíčové slovo `__asm` je oddělovač příkazů, můžete také umístit pokyny sestavení na stejný řádek:

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Všechny tři příklady generují stejný kód, ale první styl (ohraničující `__asm` blok v závorkách) obsahuje některé výhody. Složené závorky jasně oddělují kód sestavení od jazyka C++ C nebo kódu a zabraňují nutnosti opakování `__asm` klíčového slova. Složené závorky můžou také zabránit nejasnostem. Pokud chcete umístit C nebo C++ příkaz na stejný řádek jako blok `__asm`, je nutné uzavřít blok do složených závorek. Bez složených závorek nemůže kompilátor sdělit, kde se zastaví kód sestavení a C nebo C++ příkazy začnou. Proto vzhledem k tomu, že text v závorkách má stejný formát jako obyčejný MASM text, můžete snadno vyjmout a vložit text z existujících zdrojových souborů MASM.

Na rozdíl od složených závorek v C++C a, složené závorky ohraničující `__asm` blok neovlivňují rozsah proměnné. Můžete také vnořovat bloky `__asm`; Vnořování nemá vliv na rozsah proměnné.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Klíčová slova](../../cpp/keywords-cpp.md)<br/>
[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
