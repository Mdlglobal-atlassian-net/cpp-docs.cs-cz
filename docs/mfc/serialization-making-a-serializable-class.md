---
title: "Serializace: Příprava serializovatelné třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22bb8144f3c83ca98bffa2f95e73eff31ddb89be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="serialization-making-a-serializable-class"></a>Serializace: Příprava serializovatelné třídy
Pěti hlavních kroků nutné vytvořit třídu serializable. Jsou uvedeny níže a vysvětlené v následujících částech:  
  
1.  [Odvození vaší třídy z objektu CObject](#_core_deriving_your_class_from_cobject) (nebo z některé třídy odvozené od `CObject`).  
  
2.  [Přepsání – členská funkce serializace](#_core_overriding_the_serialize_member_function).  
  
3.  [Declare_serial – makro pomocí](#_core_using_the_declare_serial_macro) v deklaraci třídy.  
  
4.  [Definování konstruktor, který nemá žádné argumenty](#_core_defining_a_constructor_with_no_arguments).  
  
5.  [Implement_serial – makro v souboru implementace](#_core_using_the_implement_serial_macro_in_the_implementation_file) pro třídu.  
  
 Když zavoláte `Serialize` přímo spíše než pomocí >> a << operátorů [CArchive](../mfc/reference/carchive-class.md), poslední tři kroky nejsou potřeba pro serializaci.  
  
##  <a name="_core_deriving_your_class_from_cobject"></a>Odvození vaší třídy z objektu CObject  
 Základní serializace protokol a funkce jsou definovány v `CObject` třídy. Odvozené třídě z `CObject` (nebo z třídy odvozené od `CObject`), jak je znázorněno v následující deklaraci třídy `CPerson`, získáte přístup k serializaci protokol a funkce `CObject`.  
  
##  <a name="_core_overriding_the_serialize_member_function"></a>Přepsání serializaci – členská funkce  
 `Serialize` Členská funkce, která je definována v `CObject` třídy, je zodpovědný za ve skutečnosti serializaci data potřebná k zachycení aktuální stav daného objektu. `Serialize` Funkce má `CArchive` argument, který používá ke čtení a zápis dat objektů. [CArchive](../mfc/reference/carchive-class.md) objekt má členské funkce, `IsStoring`, která označuje, zda `Serialize` je ukládání (zápis dat) nebo načtení (čtení dat). Pomocí výsledků `IsStoring` jako vodítko, můžete buď vložit data tohoto objektu v `CArchive` objektu s operátorem vložení (**<\<**) nebo extrahovat data s operátorem extrakce ( **>>**).  
  
 Vezměte v úvahu třídu, která je odvozená od `CObject` a má dva nové proměnné členů typů `CString` a **WORD**. Následující fragment deklaraci třídy ukazuje nového člena proměnné a deklarace pro přepsané `Serialize` – členská funkce:  
  
 [!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]  
  
#### <a name="to-override-the-serialize-member-function"></a>Chcete-li přepsat serializace – členská funkce  
  
1.  Volání svou základní třídu verzi `Serialize` a ujistěte se, že zděděná část objekt serializován.  
  
2.  Vložení nebo extrahuje členské proměnné, které jsou specifické pro třídu.  
  
     Operátory vložení a extrakce komunikovat s třídou archivu číst a zapisovat data. Následující příklad ukazuje, jak implementovat `Serialize` pro `CPerson` třída deklarována výše:  
  
     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]  
  
 Můžete také [CArchive::Read](../mfc/reference/carchive-class.md#read) a [CArchive::Write](../mfc/reference/carchive-class.md#write) členské funkce pro čtení a zápis velkých objemů dat bez typu.  
  
##  <a name="_core_using_the_declare_serial_macro"></a>Pomocí declare_serial – makro  
 `DECLARE_SERIAL` Makro je nutné v deklaraci třídy, které budou podporovat serializace, jak je vidět tady:  
  
 [!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]  
  
##  <a name="_core_defining_a_constructor_with_no_arguments"></a>Definování konstruktor bez argumentů.  
 MFC vyžaduje výchozí konstruktor, pokud jej znovu vytvoří vašich objektů, jako jejich se deserializovat (načten z disku). Proces deserializace všechny proměnné členů vyplní hodnoty požadované znovu vytvořit objekt.  
  
 Veřejné, chráněný nebo privátní lze deklarovat tento konstruktor. Pokud provedete je chráněný nebo privátních, pomůže vám, ujistěte se, že se bude použit pouze pomocí funkce serializace. Konstruktor musíte umístit objekt ve stavu, který mohou být odstraněn v případě potřeby.  
  
> [!NOTE]
>  Pokud zapomenete zadat konstruktor bez argumentů ve třídě, která používá `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra, zobrazí se upozornění kompilátoru "žádný výchozí konstruktor dostupný" na řádku kde `IMPLEMENT_SERIAL` makro se používá.  
  
##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>V souboru implementace pomocí implement_serial – makro  
 `IMPLEMENT_SERIAL` Makro se používá k definování různých funkcí, třeba při odvozování serializovatelné třídy z `CObject`. Použití tohoto makra v souboru implementace (. CPP) pro třídu. První dva argumenty, které mají makro jsou název třídy a název své okamžitou základní třídy.  
  
 Třetí argument toto makro je číslo schématu. Číslo schématu je v podstatě číslo verze pro objekty třídy. Použijte celé číslo větší než nebo rovna 0 pro číslo schématu. (Nezaměňujte toto číslo schématu s terminologie databáze.)  
  
 MFC kód serializace kontroluje číslo schématu při čtení objektů do paměti. Pokud počet schématu objektu na disku neodpovídá schématu počet třídy v paměti, vyvolá výjimku knihovny `CArchiveException`, znemožňuje čtení nesprávná verze objektu vašeho programu.  
  
 Pokud chcete, aby vaše `Serialize` – členská funkce mohli přečíst více verzí – to znamená, soubory, které jsou napsané v různých verzích aplikace – můžete použít hodnotu **versionable_schema –** jako argument pro `IMPLEMENT_SERIAL` makro. Informace o využití a příklad najdete v tématu `GetObjectSchema` funkce člena třídy `CArchive`.  
  
 Následující příklad ukazuje, jak používat `IMPLEMENT_SERIAL` pro třídu, `CPerson`, který je odvozen od `CObject`:  
  
 [!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]  
  
 Jakmile máte serializovatelné třídy, může serializovat objekty třídy, jak je popsáno v článku [serializace: serializace objektu](../mfc/serialization-serializing-an-object.md).  
  
## <a name="see-also"></a>Viz také  
 [Serializace](../mfc/serialization-in-mfc.md)

