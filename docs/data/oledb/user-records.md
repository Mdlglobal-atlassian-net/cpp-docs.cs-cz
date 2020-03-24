---
title: Uživatelské záznamy
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: 94a70b48793d44eda4fd76d9b59460418cfbc032
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209440"
---
# <a name="user-records"></a>Uživatelské záznamy

> [!NOTE]
> Průvodce příjemcem OLE DB ATL není v aplikaci Visual Studio 2019 a novějších k dispozici. Tuto funkci můžete přesto přidat ručně. Další informace najdete v tématu [Vytvoření příjemce bez použití Průvodce](creating-a-consumer-without-using-a-wizard.md).

Pro použití statického přístupového objektu (to znamená přistupující objekt odvozený z `CAccessor`) musí mít váš příjemce záznam uživatele. Záznam uživatele je C++ třída, která obsahuje datové prvky pro zpracování vstupu nebo výstupu. **Průvodce příjemcem OLE DB ATL** vygeneruje uživatelský záznam pro vašeho příjemce. Do záznamu uživatele můžete přidat metody pro volitelné úlohy, jako jsou příkazy pro zpracování.

Následující kód ukazuje vzorový záznam, který zpracovává příkazy. V záznamu uživatele BEGIN_COLUMN_MAP představuje datovou sadu, která byla předána příjemci od poskytovatele. BEGIN_PARAM_MAP představuje sadu parametrů příkazu. Tento příklad používá třídu [CCommand](../../data/oledb/ccommand-class.md) ke zpracování parametrů příkazu. Datové členy v položkách mapy reprezentují posuny do jednoho souvislého bloku paměti pro každou instanci třídy. COLUMN_ENTRY makra odpovídají PROVIDER_COLUMN_ENTRYm makrům na straně poskytovatele.

Další informace o makrech COLUMN_MAP a PARAM_MAP naleznete v tématu [makra pro OLE DB šablony zákazníků](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>Záznamy uživatelů generovaných průvodcem

Použijete-li **Průvodce příjemcem OLE DB ATL** k vygenerování příjemce, máte možnost použít šablony OLE DB nebo atributy OLE DB. Vygenerovaný kód se v každém případě liší. Další informace o tomto kódu naleznete v tématu [třídy generované průvodcem příjemce](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Podpora záznamu uživatelů pro více přístupových objektů

Podrobné informace o scénářích, ve kterých potřebujete použít více přístupových objektů, naleznete v tématu [použití více přístupových objektů pro sadu řádků](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

Následující příklad ukazuje záznam uživatele upravený tak, aby podporoval více přístupových objektů pro sadu řádků. Místo BEGIN_COLUMN_MAP a END_COLUMN_MAP používá pro každý přistupující objekt [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) a [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) . BEGIN_ACCESSOR makro Určuje číslo přistupujícího objektu (posun od nuly) a zda je přistupující objekt autoaccesser. Autoaccesss volá `GetData` pro automatické načtení dat při volání metody [MoveNext](../../data/oledb/crowset-movenext.md). Neautomatické přistupující objekty vyžadují, abyste data explicitně načetli. Pokud vytváříte vazbu k velkému datovému poli (například k rastrovému obrázku), který nechcete načíst pro každý záznam, použijte neautomatický přistupující objekt.

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)
