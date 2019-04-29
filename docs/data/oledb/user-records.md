---
title: Uživatelské záznamy
ms.date: 10/22/2018
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
ms.openlocfilehash: 5dd7be3eccd59dc1a5a0dc1cd6932ca1310627c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389044"
---
# <a name="user-records"></a>Uživatelské záznamy

Pro použití statického následovníka (to znamená, přístupový objekt odvozený od `CAccessor`), vaše spotřebitel musí mít uživatelský záznam. Záznam uživatele je třída C++, který obsahuje prvky dat ke zpracování vstupu nebo výstupu. **Průvodce příjemcem ATL OLE DB** generuje záznam uživatele pro vaše příjemce. Přidat metody do uživatelského záznamu pro volitelné úkoly, jako je zpracování příkazů.

Následující kód ukazuje ukázkové záznam, který zpracovává příkazy. V záznamu uživatele BEGIN_COLUMN_MAP představuje sadu řádků data předaná příjemci z zprostředkovatele. BEGIN_PARAM_MAP představuje sadu parametrů příkazu. Tento příklad používá [CCommand](../../data/oledb/ccommand-class.md) třídy pro zpracování parametry příkazu. Datové členy v mapě položky představují posun do souvislý blok paměti pro každou instanci třídy. COLUMN_ENTRY makra odpovídají PROVIDER_COLUMN_ENTRY makra na straně zprostředkovatele.

Další informace o COLUMN_MAP a PARAM_MAP najdete v tématu [makra pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

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

## <a name="wizard-generated-user-records"></a>Generované průvodcem uživatelských záznamů

Pokud používáte **průvodce příjemcem ATL OLE DB** generovat příjemce, máte na výběr mezi používáním šablony technologie OLE DB nebo OLE DB atributy. Generovaný kód je v každém případě liší. Další informace o tomto kódu najdete v tématu [vygenerované třídy](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Podpora uživatelského záznamu pro několik přístupových objektů

Podrobné informace o scénářích, ve kterých je potřeba použít několik přístupových objektů, naleznete v tématu [použití více přístupových objektů pro sadu řádků](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

Následující příklad ukazuje záznam uživatele, pro podporu více přístupových objektů v dané sadě řádků změnit. Místo BEGIN_COLUMN_MAP a END_COLUMN_MAP používá [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) a [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) pro každý přistupující objekt. BEGIN_ACCESSOR – makro Určuje číslo přístupového objektu (posun od nuly) a zda je přistupující objekt automaticky přistupující objekt. Volání načtel `GetData` k načtení dat automaticky na volání [MoveNext](../../data/oledb/crowset-movenext.md). Manuální přístupových objektů vyžadují, abyste explicitně načíst data. Pokud provádíte navázání na pole velkých objemů dat (např. rastrový obrázek), které možná nebudete chtít načíst pro každý záznam, použijte manuální přistupující objekt.

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

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)