---
title: Předávání typů (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: 0803ecc2ffb2da2748b1ef063481aa2571f27f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171928"
---
# <a name="type-forwarding-ccli"></a>Předávání typů (C++/CLI)

*Přesměrování typu* umožňuje přesunout typ z jednoho sestavení (sestavení a) do jiného sestavení (sestavení B), což znamená, že není nutné znovu kompilovat klienty, které používají sestavení a.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Tato funkce není podporována v prostředí Windows Runtime.

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Následující příklad kódu ukazuje, jak používat předávání typů.

### <a name="syntax"></a>Syntaxe

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Parametry

*new*<br/>
Sestavení, do kterého přesouváte definici typu.

*type*<br/>
Typ, jehož definice se přesouváte do jiného sestavení.

### <a name="remarks"></a>Poznámky

Po dodání komponenty (sestavení) a jejich použití klientskými aplikacemi můžete použít předávání typů k přesunutí typu ze součásti (sestavení) do jiného sestavení, odeslání aktualizované součásti (a všech dalších potřebných sestavení) a klienta. aplikace budou i nadále fungovat bez nutnosti jejich kompilace.

Přesměrování typu funguje jenom pro součásti, na které odkazuje stávající aplikace. Při opětovném sestavování aplikace musí existovat odpovídající odkazy na sestavení pro všechny typy používané v aplikaci.

Při předávání typu (typu A) ze sestavení je nutné přidat atribut `TypeForwardedTo` pro daný typ a také odkaz na sestavení. Sestavení, na které odkazujete, musí obsahovat jednu z následujících možností:

- Definice pro typ A.

- Atribut `TypeForwardedTo` pro typ A, jakož i odkaz na sestavení.

Mezi příklady typů, které lze přesměrováním zahrnout:

- třídy ref

- třídy hodnot

- výčty

- rozhraní

Nemůžete přeslat následující typy:

- Obecné typy

- Nativní typy

- Vnořené typy (Pokud chcete předávání vnořeného typu, byste měli přepředt nadřazený typ)

Typ můžete přeslat do sestavení vytvořeného v jakémkoli jazyce, který cílí na modul CLR (Common Language Runtime).

Takže pokud soubor zdrojového kódu, který se používá k sestavení sestavení A. dll obsahuje definici typu (`ref class MyClass`), a chtěli jste přesunout tuto definici typu do sestavení B. dll, měli byste:

1. Přesuňte definici typu `MyClass` do souboru zdrojového kódu, který se používá k sestavení B. dll.

2. Sestavit sestavení B. dll

3. Odstraňte definici typu `MyClass` ze zdrojového kódu, který se používá k sestavení knihovny DLL, a nahraďte ji následujícím kódem:

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Sestavte sestavení A. dll.

5. Použijte soubor. dll bez opětovné kompilace klientských aplikací.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`
