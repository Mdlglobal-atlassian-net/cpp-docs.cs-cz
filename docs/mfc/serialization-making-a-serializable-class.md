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
ms.openlocfilehash: 9648bd4f516a5f174534336b1ca3b42bb51ca0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372708"
---
# <a name="serialization-making-a-serializable-class"></a>Serializace: Příprava serializovatelné třídy

K tomu, aby byla třída serializovatelná, je zapotřebí pět hlavních kroků. Jsou uvedeny níže a vysvětleny v následujících částech:

1. [Odvození třídy z CObject](#_core_deriving_your_class_from_cobject) (nebo z některé `CObject`třídy odvozené z).

1. [Přepsání členské funkce Serializovat](#_core_overriding_the_serialize_member_function).

1. [Použití DECLARE_SERIAL makro](#_core_using_the_declare_serial_macro) v deklaraci třídy.

1. [Definování konstruktoru, který nepřijímá žádné argumenty](#_core_defining_a_constructor_with_no_arguments).

1. [Použití IMPLEMENT_SERIAL makra v souboru implementace](#_core_using_the_implement_serial_macro_in_the_implementation_file) pro vaši třídu.

Pokud voláte `Serialize` přímo, nikoli prostřednictvím >> a << operátory [CArchive](../mfc/reference/carchive-class.md), poslední tři kroky nejsou vyžadovány pro serializaci.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a>Odvození vaší třídy z CObject

Základní serializační protokol a funkce jsou `CObject` definovány ve třídě. Odvozením třídy z `CObject` (nebo z třídy `CObject`odvozené z ), jak `CPerson`je znázorněno v následujícím prohlášení třídy , získáte přístup k protokolu serializace a funkce `CObject`.

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a>Přepsání funkce Serializovat členy

Členská `Serialize` funkce, která je `CObject` definována ve třídě, je zodpovědná za skutečné serializaci dat nezbytných k zachycení aktuálního stavu objektu. Funkce `Serialize` má `CArchive` argument, který používá ke čtení a zápisu dat objektu. CArchive Objekt má členská `IsStoring`funkce , `Serialize` která označuje, zda je ukládání (zápis dat) nebo načítání (čtení dat). [CArchive](../mfc/reference/carchive-class.md) Pomocí výsledků `IsStoring` jako vodítko vložíte data objektu do `CArchive` objektu pomocí operátoru**<** vložení ( ) nebo**>>** extrahujete data s operátorem extrakce ( ).

Zvažte třídu, která `CObject` je odvozena od a `CString` má dvě nové členské proměnné, typů a **WORD**. Následující fragment deklarace třídy zobrazuje nové členské proměnné `Serialize` a deklaraci pro potlačenou členskou funkci:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Přepsání členské funkce Serializovat

1. Zavolejte verzi základní `Serialize` třídy a ujistěte se, že zděděná část objektu je serializována.

1. Vložte nebo extrahujte členské proměnné specifické pro vaši třídu.

   Vkládání a extrakce operátory komunikovat s třídou archivu číst a zapisovat data. Následující příklad ukazuje, `Serialize` jak `CPerson` implementovat pro výše deklarovanou třídu:

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Můžete také použít [CArchive::Read](../mfc/reference/carchive-class.md#read) a [CArchive::Write](../mfc/reference/carchive-class.md#write) členské funkce pro čtení a zápis velkého množství netypových dat.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a>Použití DECLARE_SERIAL makra

Makro DECLARE_SERIAL je vyžadováno v deklaraci tříd, které budou podporovat serializaci, jak je znázorněno zde:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a>Definování konstruktoru bez argumentů

Knihovna MFC vyžaduje výchozí konstruktor při opětovném vytvoření objektů při jejich dekonstruaci (načtené z disku). Proces deserializace vyplní všechny členské proměnné hodnotami potřebnými k opětovnému vytvoření objektu.

Tento konstruktor může být deklarován jako veřejný, chráněný nebo soukromý. Pokud jej provedete chráněné nebo soukromé, můžete zajistit, že bude použit pouze serializace funkce. Konstruktor musí umístit objekt do stavu, který umožňuje jeho odstranění v případě potřeby.

> [!NOTE]
> Pokud zapomenete definovat konstruktor bez argumentů ve třídě, která používá DECLARE_SERIAL a IMPLEMENT_SERIAL makra, zobrazí se upozornění kompilátoru "žádný výchozí konstruktor" na řádku, kde se používá IMPLEMENT_SERIAL makro.

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>Použití IMPLEMENT_SERIAL makra v implementačním souboru

Makro IMPLEMENT_SERIAL se používá k definování různých funkcí potřebných při `CObject`odvození serializovatelné třídy z aplikace . Toto makro se používá v souboru implementace (. CPP) pro vaši třídu. První dva argumenty pro makro jsou název třídy a název její okamžité základní třídy.

Třetím argumentem tohoto makra je číslo schématu. Číslo schématu je v podstatě číslo verze pro objekty třídy. Pro číslo schématu použijte celé číslo větší nebo rovné 0. (Nezaměňujte toto číslo schématu s terminologií databáze.)

Kód serializace knihovny MFC zkontroluje číslo schématu při čtení objektů do paměti. Pokud číslo schématu objektu na disku neodpovídá číslo schématu třídy v paměti, knihovna `CArchiveException`vyvolá , brání programu ve čtení nesprávné verze objektu.

Pokud chcete, `Serialize` aby vaše členská funkce mohla číst více verzí , můžete hodnotu *VERSIONABLE_SCHEMA* použít jako argument pro makro IMPLEMENT_SERIAL. Informace o použití a příklad `GetObjectSchema` naleznete v `CArchive`členské funkci třídy .

Následující příklad ukazuje, jak používat IMPLEMENT_SERIAL `CPerson`pro třídu `CObject`, která je odvozena z :

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Jakmile máte serializovatelné třídy, můžete serializovat objekty třídy, jak je popsáno v článku [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Viz také

[Serializace](../mfc/serialization-in-mfc.md)
