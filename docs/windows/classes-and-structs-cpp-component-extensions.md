---
title: Třídy a struktury (C++ Component Extensions) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9863786e5e017b69217f984e3aa6d1db597e74d3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="classes-and-structs--c-component-extensions"></a>Třídy a struktury (rozšíření komponent C++)
Deklaruje třídě nebo struktuře jejichž *doba života objektu* je spravována automaticky. Pokud objekt již není dostupný nebo mimo rozsah, Visual C++ automaticky zahodí paměti, který je přidělen k objektu.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Syntaxe**  
  
```  
  
      class_access  
      ref class  
      name  
      modifier :  inherit_accessbase_type {};  
class_accessref structnamemodifier :  inherit_accessbase_type {};  
class_accessvalue classnamemodifier :  inherit_accessbase_type {};  
class_accessvalue structnamemodifier :  inherit_accessbase_type {};  
  
```  
  
 **Parametry**  
  
 *class_access* (volitelné)  
 Usnadnění přístupu třídě nebo struktuře mimo sestavení. Možné hodnoty jsou **veřejné** a `private` (`private` je výchozí nastavení). Vnořené třídy nebo struktury nemůže mít *class_access* specifikátor.  
  
 *Jméno*  
 Název třídě nebo struktuře.  
  
 *Modifikátor* (volitelné)  
 [abstraktní](../windows/abstract-cpp-component-extensions.md) a [zapečetěné](../windows/sealed-cpp-component-extensions.md) jsou platné modifikátory.  
  
 *inherit_access* (volitelné)  
 Usnadnění přístupu `base_type`. Je pouze povolené usnadnění `public` (`public` je výchozí nastavení).  
  
 *base_type* (volitelné)  
 Základní typ. Typ hodnoty se ale nemůže fungovat jako základní typ.  
  
 Další informace najdete v popisech konkrétní jazyk tohoto parametru v prostředí Windows Runtime a běžné Runtimesections jazyk.  
  
 **Poznámky**  
  
 Výchozí člen usnadnění objektu deklarovat s **ref třída** nebo **třídy hodnoty** je `private`. A usnadnění výchozí člen objektu deklarovat s **ref struct** nebo **hodnotu struktura** je `public`.  
  
 Když odkazového typu dědí z jiného typu odkaz, virtuální funkce v základní třídě explicitně se musí přepsat (s [přepsat](../windows/override-cpp-component-extensions.md)) nebo skryté (s [new (nový slot v tabulce vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). Funkce odvozené třídy musí být explicitně označeny také jako `virtual`.  
  
 K detekci v době kompilace, jestli je typ `ref class` nebo `ref struct`, nebo `value class` nebo `value struct`, použijte `__is_ref_class (type)`, `__is_value_class (type)`, nebo `__is_simple_value_class (type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Další informace o třídy a struktury najdete v tématu  
  
-   [Vytváření instancí třídy a struktury](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
 
  
-   [Sémantika zásobníku C++ pro typy odkazů](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [Tříd, struktur a sjednocení](../cpp/classes-and-structs-cpp.md)  
  
-   [Destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)  
  
-   [Uživatelem definované operátory (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [Uživatelem definované převody (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [Postupy: Zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [Obecné třídy (C++/CLI)](../windows/generic-classes-cpp-cli.md)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 V tématu [Ref třídy a struktury](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx) a [hodnota třídy a struktury](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx).  
  
 **Parametry**  
  
 *base_type* (volitelné)  
 Základní typ. A `ref class` nebo `ref struct` může dědit vlastnosti z nula nebo více rozhraní a nula nebo jedna `ref` typy. A `value class` nebo `value struct` může dědit vlastnosti pouze z nula nebo více rozhraní.  
  
 Pokud deklarace objektu pomocí `ref class` nebo `ref struct` klíčová slova, objekt přistupuje popisovač pro objekt; to znamená, ukazatel čítač odkaz na objekt. Pokud proměnnou deklarované ocitne mimo obor, kompilátor automaticky odstraní podkladových objektů. Pokud se objekt se používá jako parametr v volání nebo je uložené v proměnné, popisovač pro objekt je ve skutečnosti předán nebo uložené.  
  
 Pokud deklarace objektu pomocí `value class` nebo `value struct` klíčová slova, doba života objektu deklarované objektu není pod dohledem. Objekt je jako všechny ostatní standardní C++ třídě nebo struktuře.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 V následující tabulce jsou uvedeny rozdíly v syntaxi uvedenou v **všechny moduly runtime** část, která jsou specifická pro C + +/ CLI.  
  
 **Parametry**  
  
 *base_type* (volitelné)  
 Základní typ. A `ref class` nebo `ref struct` může dědit vlastnosti z nula nebo více spravovaných rozhraní a nula nebo jeden ref typy. A `value class` nebo `value struct` může dědit vlastnosti pouze z nula nebo více spravovaných rozhraní.  
  
 `ref class` a `ref struct` klíčová slova oznámení kompilátoru, která třídu nebo strukturu je přidělování v haldě. Pokud se objekt se používá jako parametr v volání nebo je uložené v proměnné, odkaz na objekt je ve skutečnosti předán nebo uložené.  
  
 `value class` a `value struct` klíčová slova informuje kompilátor, že je hodnota přidělené třídu nebo strukturu se předají funkcím nebo členů.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)