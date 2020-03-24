---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180222"
---
# <a name="__declspec"></a>__declspec

**Specifické pro společnost Microsoft**

Syntaxe rozšířeného atributu pro určení informací o třídě úložiště používá klíčové slovo **__declspec** , které určuje, že instance daného typu bude uložena s atributem třídy úložiště specifické pro společnost Microsoft, který je uveden níže. Příklady dalších modifikátorů třídy úložiště zahrnují klíčová slova **static** a **extern** . Tato klíčová slova jsou však součástí specifikace ANSI jazyků C a C++ a jako taková nejsou zahrnuta v syntaxi doplňkového atributu. Syntaxe rozšířeného atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyků C a C++.

## <a name="grammar"></a>Gramatika

*specifikátor prohlášení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Rozšířené-prohlášení-modifikátor-SEQ* **)**

*Rozšířená – modifikátor-SEQ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Rozšířené-prohlášení-modifikátor*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Rozšířené-prohlášení-modifikátor* *Rozšířené* ------modifikátor-SEQ

*Rozšířené-prohlášení – modifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Zarovnání (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocate ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;**přidělování** &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**AppDomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zastaralé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**holé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jiným**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**inline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**throw**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;tabulce **vtable**<br/>
**proces** &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;**vlastnost &nbsp;(** { **Get =** _get_func_name_ &#124; **; Put =** _put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omezit**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre (nezmírňování)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vlákno**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *ComObjectGUID* **")**

Mezera odděluje sekvenci modifikátoru deklarace. Příklady se zobrazí v pozdějších oddílech.

Gramatika rozšířeného atributu podporuje tyto atributy třídy úložiště specifické pro společnost Microsoft [: Zarovnat](../cpp/align-cpp.md), přidělit [allocator](../cpp/allocator.md), [přidělovat](../cpp/allocate.md), [AppDomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [zastaralé](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [holé](../cpp/naked-cpp.md), [jiné](../cpp/noalias.md), [nevloženo](../cpp/noinline.md), [return](../cpp/noreturn.md), [unthrow](../cpp/nothrow-cpp.md), typu [vtable](../cpp/novtable.md), [Process](../cpp/process.md), [restrict](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [ Spectre](../cpp/spectre.md)a [thread](../cpp/thread.md). Také podporuje tyto atributy objektu COM: [Property](../cpp/property-cpp.md) a [UUID](../cpp/uuid-cpp.md).

Atributy třídy úložiště **code_seg** **,** **dllexport**, **dllimport**, **selectany** **,** **thread**a **nothrow** **UUID** jsou vlastnosti pouze z deklarace objektu nebo **funkce, na**kterou jsou aplikovány **, do**vlastností. Atribut **thread** ovlivňuje pouze data a objekty. Atributy **holé** a **Spectre** ovlivňují pouze funkce. Atributy **dllimport** a **dllexport** ovlivňují funkce, data a objekty. Atributy **vlastnosti**, **selectany**a **UUID** ovlivňují objekty modelu COM.

Z důvodu kompatibility s předchozími verzemi je **_declspec** synonymem pro **__declspec** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

Klíčová slova **__declspec** by se měla umístit na začátek jednoduché deklarace. Kompilátor ignoruje bez upozornění všechna **__declspec** klíčová slova, která jsou umístěna za * nebo & a před identifikátorem proměnné v deklaraci.

Atribut **__declspec** zadaný na začátku deklarace uživatelsky definovaného typu se vztahuje na proměnnou daného typu. Příklad:

```cpp
__declspec(dllimport) class X {} varX;
```

V tomto případě se atribut vztahuje na `varX`. Atribut **__declspec** umístěný po použití klíčového slova **Class** nebo **struct** na uživatelsky definovaný typ. Příklad:

```cpp
class __declspec(dllimport) X {};
```

V tomto případě se atribut vztahuje na `X`.

Obecný návod pro použití atributu **__declspec** pro jednoduché deklarace je následující:

*prohlášení-specifikátor-SEQ* *init-deklarátor-list*;

*Specifikátor deklarace-SEQ* by měl obsahovat mimo jiné základní typ (například **int**, **float**, **typedef**nebo název třídy), třídu úložiště (například **static**, **extern**) nebo rozšíření **__declspec** . *Příkaz init-deklarátor-list* by měl obsahovat mimo jiné část deklarace s ukazatelem. Příklad:

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

Následující kód deklaruje místní proměnnou vlákna integer a inicializuje ji hodnotou:

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)
