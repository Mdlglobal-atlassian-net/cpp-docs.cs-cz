---
title: __declspec | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f413c56b665a1878fb1e948b975ab8e4cbc0daf4
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163581"
---
# <a name="declspec"></a>__declspec

**Specifické pro Microsoft**

Syntaxe rozšířeného atributu pro určení informací o třídě úložiště používá **__declspec** – klíčové slovo, které určuje, že instance daného typu uloží v rámci níže uvedeného atributu třídy úložiště specifické pro společnost Microsoft. Příklady dalších modifikátorů na úložiště **statické** a **extern** klíčová slova. Tato klíčová slova jsou však součástí specifikace ANSI jazyků C a C++ a jako taková nejsou zahrnuta v syntaxi doplňkového atributu. Syntaxe rozšířeného atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyků C a C++.

## <a name="grammar"></a>Gramatika

*decl-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*Extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl modifikátor*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl modifikátor* *extended-decl-modifier-seq*

*Extended-decl modifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zarovnání (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**přidělit ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**domény aplikace**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zastaralé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Proces**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vlastnosti (** { **získat =**_get_func_name_ &#124; **, vložení =**_put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omezení**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre(nomitigation)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vlákno**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *ComObjectGUID* **")**

Mezera odděluje sekvenci modifikátoru deklarace. Příklady se zobrazí v pozdějších oddílech.

Rozšířený atribut gramatiky podporuje tyto atributy třídy úložiště specifické pro společnost Microsoft: [zarovnat](../cpp/align-cpp.md), [přidělit](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [zastaralé](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [procesu](../cpp/process.md), [omezit](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [chyby zabezpečení spectre](../cpp/spectre.md), a [vlákno](../cpp/thread.md). Také podporuje tyto atributy objektu COM: [vlastnost](../cpp/property-cpp.md) a [uuid](../cpp/uuid-cpp.md).

**Code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **vlastnost**, **omezit**, **selectany**, **vlákno**, a **uuid**atributy třídy úložiště jsou vlastnosti pouze prohlášení objektu nebo funkce, do které se použijí. **Vlákno** atribut má vliv na data a pouze objekty. **Naked** a **chyby zabezpečení spectre** atributy ovlivňují pouze funkce. **Dllimport** a **dllexport** ovlivňují atributy funkce, data a objekty. **Vlastnost**, **selectany**, a **uuid** objekty COM ovlivňují atributy.

Z důvodu kompatibility s předchozími verzemi **_declspec** je synonymum pro **__declspec** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

**__Declspec** klíčová slova, umístit na začátek jednoduchého prohlášení. Kompilátor ignoruje bez varování všechna **__declspec** klíčová slova umístí po * nebo & a před identifikátorem proměnné v deklaraci.

A **__declspec** atribut na začátku deklarace uživatelského typu platí pro proměnnou daného typu. Příklad:

```cpp
__declspec(dllimport) class X {} varX;
```

V tomto případě platí atribut pro `varX`. A **__declspec** atribut umístěný za **třídy** nebo **struktura** – klíčové slovo platí pro typ definovaný uživatelem. Příklad:

```cpp
class __declspec(dllimport) X {};
```

V tomto případě platí atribut pro `X`.

Obecný návod pro použití **__declspec** atribut pro jednoduché deklarace je následující:

*decl-specifier-seq* *init-declarator-list*;

*Decl-specifier-seq* by měl obsahovat mimo jiné i základní typ (například **int**, **float**, **typedef**, nebo název třídy), Třída úložiště (třeba **statické**, **extern**), nebo **__declspec** rozšíření. *Init-declarator-list* by měl obsahovat mimo jiné část deklarace s ukazatelem. Příklad:

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)