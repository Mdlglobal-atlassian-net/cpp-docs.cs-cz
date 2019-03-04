---
title: 'Serializace: Příprava serializovatelné třídy'
ms.date: 11/04/2016
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
ms.openlocfilehash: 995744381c8f82dc637e4aa0452e37af170b168b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281457"
---
# <a name="serialization-making-a-serializable-class"></a>Serializace: Příprava serializovatelné třídy

Pět hlavních kroků je potřeba vytvořit třídu serializovatelný. Jsou uvedené níže a vysvětlené v následujících částech:

1. [Odvození vaší třídy z objektu CObject](#_core_deriving_your_class_from_cobject) (nebo z některé třídy odvozené od `CObject`).

1. [Přepsání členskou funkci Serialize](#_core_overriding_the_serialize_member_function).

1. [Pomocí DECLARE_SERIAL – makro](#_core_using_the_declare_serial_macro) v deklaraci třídy.

1. [Definovat konstruktor, který nepřijímá žádné argumenty](#_core_defining_a_constructor_with_no_arguments).

1. [V souboru implementace pomocí IMPLEMENT_SERIAL – makro](#_core_using_the_implement_serial_macro_in_the_implementation_file) pro vaši třídu.

Při volání `Serialize` přímo namísto prostřednictvím >> a << provozovatelé [CArchive](../mfc/reference/carchive-class.md), poslední tři kroky nejsou nutné k serializaci.

##  <a name="_core_deriving_your_class_from_cobject"></a> Odvození vaší třídy z objektu CObject

Základní serializace protokol a funkce jsou definovány v `CObject` třídy. Odvozením z vaší třídy `CObject` (nebo z třídy odvozené od `CObject`), jak je znázorněno v následující deklaraci třídy `CPerson`, můžete získat přístup k protokolu serializace a funkčnost `CObject`.

##  <a name="_core_overriding_the_serialize_member_function"></a> Přepsání serializaci členská funkce

`Serialize` Členskou funkci, která je definována v `CObject` třídy, je zodpovědná za serializaci ve skutečnosti data potřebná pro zachycení aktuálního stavu objektu. `Serialize` Funkce má `CArchive` argument, který se používá ke čtení a zápis dat objektů. [CArchive](../mfc/reference/carchive-class.md) objekt má členská funkce `IsStoring`, což znamená, zda `Serialize` je ukládat (zápis dat) a načítání (čtení dat). Pomocí výsledků `IsStoring` jako vodítko, můžete buď vložit dat tohoto objektu v `CArchive` objektu pomocí operátoru vložení (**<\<**) ani je nemohl extrahovat data s operátorem extrakce ( **>>**).

Vezměte v úvahu třídu, která je odvozena od `CObject` a má dva nové proměnné členů typů `CString` a **slovo**. Následující fragment deklarace třídy ukazuje nový člen, proměnné a deklarace přepsané `Serialize` členské funkce:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Chcete-li přepsat členskou funkci Serialize

1. Volání základní třídy verzi `Serialize` abyste měli jistotu, že zděděná část objekt serializován.

1. Vložit nebo extrahovat členské proměnné, které jsou specifické pro vaší třídy.

   Operátory vkládání a extrakci pracovat s třídou archivu číst a zapisovat data. Následující příklad ukazuje, jak implementovat `Serialize` pro `CPerson` třídy deklarované výše:

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Můžete také použít [CArchive::Read](../mfc/reference/carchive-class.md#read) a [CArchive::Write](../mfc/reference/carchive-class.md#write) členské funkce pro čtení a zápis velkých objemů dat bez typu.

##  <a name="_core_using_the_declare_serial_macro"></a> Pomocí DECLARE_SERIAL – makro

DECLARE_SERIAL – makro je požadováno v deklaraci třídy, které budou podporovat serializace, jak je znázorněno zde:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

##  <a name="_core_defining_a_constructor_with_no_arguments"></a> Definování konstruktor bez argumentů.

MFC vyžaduje výchozí konstruktor, pokud znovu vytvoří objekty podle jejich se deserializovat (načtené z disku). Proces deserializace vyplní všechny proměnné členů hodnotami, které je potřeba znovu vytvořit objekt.

Tento konstruktor může použít deklaraci public, protected nebo private. Pokud ji nastavíte chráněná nebo privátní, Nápověda, ujistěte se, že ho se používat pouze funkce serializace. Konstruktor musí objekt umístit na stavu, který umožňuje v případě potřeby odstranit.

> [!NOTE]
>  Pokud zapomenete definovat konstruktor bez argumentů do třídy, která používá DECLARE_SERIAL a IMPLEMENT_SERIAL makra, zobrazí se upozornění kompilátoru "žádný výchozí konstruktor. k dispozici" na řádku, kde se používá IMPLEMENT_SERIAL – makro.

##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> V souboru implementace pomocí IMPLEMENT_SERIAL – makro

IMPLEMENT_SERIAL – makro se používá k definování různých funkcí, třeba když odvozujete serializovatelné třídy z `CObject`. Použijte toto makro v souboru implementace (. CPP) pro vaši třídu. První dva argumenty, které mají makra jsou název třídy a název její přímé základní třídy.

Třetí argument toto makro je číslo schématu. Číslo schématu je v podstatě číslo verze pro objekty třídy. Pro číslo schématu používejte celé číslo větší než nebo rovna 0. (Nezaměňujte toto číslo schématu s terminologií databáze.)

Serializační kód knihovny MFC zkontroluje číslo schéma při čtení objektů do paměti. Pokud číslo schématu objektu na disku neodpovídá schématu počet tříd v paměti, vyvolá výjimku knihovny `CArchiveException`, programu brání čtení nesprávnou verzi objektu.

Pokud chcete, aby vaše `Serialize` členské funkce bude moct číst více verzí – to znamená, soubory, které jsou napsané v různých verzích aplikace – můžete použít hodnotu *VERSIONABLE_SCHEMA* jako argument IMPLEMENT_SERIAL makra. Informace o využití a příklad najdete v tématu `GetObjectSchema` členské funkce třídy `CArchive`.

Následující příklad ukazuje způsob použití třídy IMPLEMENT_SERIAL `CPerson`, která je odvozena z `CObject`:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Jakmile budete mít serializovatelné třídy, může serializovat objekty třídy, jak je popsáno v článku [serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Viz také:

[Serializace](../mfc/serialization-in-mfc.md)
