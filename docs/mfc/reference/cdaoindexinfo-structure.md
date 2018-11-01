---
title: CDaoIndexInfo – struktura
ms.date: 06/25/2018
f1_keywords:
- CDaoIndexInfo
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
ms.openlocfilehash: 55f64fcebc308bd0e63643cfb5447608c4e2e37c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677900"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo – struktura

`CDaoIndexInfo` Struktura obsahuje informace o objektu indexu definované pro datový přístup k objektům (DAO).

## <a name="syntax"></a>Syntaxe

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
    CString m_strName;                  // Primary
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary
    short m_nFields;                    // Primary
    BOOL m_bPrimary;                    // Secondary
    BOOL m_bUnique;                     // Secondary
    BOOL m_bClustered;                  // Secondary
    BOOL m_bIgnoreNulls;                // Secondary
    BOOL m_bRequired;                   // Secondary
    BOOL m_bForeign;                    // Secondary
    long m_lDistinctCount;              // All

    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

### <a name="parameters"></a>Parametry

*m_strName*<br/>
Pole objektu jedinečné názvy. Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_pFieldInfos*<br/>
Ukazatel na pole [cdaoindexfieldinfo –](../../mfc/reference/cdaoindexfieldinfo-structure.md) objekty označující pole, která tabledef nebo sady záznamů jsou klíčová pole v indexu. Každý objekt identifikuje jedno pole v indexu. Je výchozí index řazení vzestupně. Objekt indexu může mít jednoho nebo více polí představující klíče indexu pro každý záznam. Toto může být vzestupné řazení sestupně, nebo jejich kombinaci.

*m_nFields*<br/>
Počet polí, které jsou uložené v `m_pFieldInfos`.

*m_bPrimary*<br/>
Pokud primární vlastnost nastavena na hodnotu TRUE, index objekt představuje primární index. Primární index se skládá z jednoho nebo více polí, které jedinečně identifikují všechny záznamy v tabulce v předdefinovaném pořadí. Protože index pole musí být jedinečné, jedinečné vlastnosti objektu indexu je také nastavena na hodnotu TRUE v rozhraní DAO. Pokud primární index tvořen více než jedno pole, každé pole může obsahovat duplicitní hodnoty, ale kombinace hodnot z indexovaného pole musí být jedinečný. Primární index se skládá z klíče pro tabulku a obvykle obsahuje stejné pole jako primární klíč.

Když nastavíte primární klíč u tabulky, primární klíč je automaticky definovaný jako primární index pro tabulku. Další informace najdete v tématech "Primární vlastnosti" a "Jedinečné vlastnosti" v nápovědě k DAO.

> [!NOTE]
> Může existovat, maximálně jeden primární index u tabulky.

*m_bUnique*<br/>
Označuje, zda objekt index představuje jedinečný index pro tabulku. Pokud je tato vlastnost hodnotu TRUE, představuje objekt indexu, který je jedinečný index. Jedinečný index se skládá z jednoho nebo více polí, které logicky uspořádat všechny záznamy v tabulce v pořadí jedinečné, předdefinované. Pokud jedno pole obsahuje index, hodnoty v tomto poli musí být jedinečné pro celou tabulku. Pokud je index tvořen více než jedno pole, každé pole může obsahovat duplicitní hodnoty, ale kombinace hodnot z indexovaného pole musí být jedinečný.

Pokud primární i jedinečné vlastnosti objektu indexu jsou nastavena na hodnotu TRUE, index je jedinečný a primární: jednoznačně identifikuje všechny záznamy v tabulce v předdefinované logické pořadí. Pokud je primární vlastnost nastavena na hodnotu FALSE, index je sekundární index. Sekundární indexy (klíče a nonkey) logicky uspořádat záznamy v předdefinovaném pořadí bez slouží jako identifikátor pro záznamy v tabulce.

Další informace najdete v tématech "Primární vlastnosti" a "Jedinečné vlastnosti" v nápovědě k DAO.

*m_bClustered*<br/>
Označuje, zda objekt index představuje clusterovaný index pro tabulku. Pokud je tato vlastnost hodnotu TRUE, index objekt představuje clusterovaný index; v ostatních případech tomu tak není. Clusterovaný index se skládá z jednoho nebo více nonkey polí, které, dohromady, uspořádat všechny záznamy v tabulce v předdefinovaném pořadí. Pomocí clusterovaného indexu data v tabulce doslova uložené v pořadí určeném clusterovaný index. Clusterovaný index poskytuje efektivní přístup k záznamům v tabulce. Další informace naleznete v tématu "Clusterovaný vlastnost" v nápovědě k DAO.

> [!NOTE]
> Skupinový vlastnost se ignoruje u databází, které používají databázovém stroji Microsoft Jet vzhledem k tomu, že databázový stroj nepodporuje Clusterované indexy.

*m_bIgnoreNulls*<br/>
Určuje, zda jsou položky index pro záznamy, jejichž hodnoty Null v jejich rejstřík polí. Pokud je tato vlastnost hodnotu TRUE, pole s hodnotami Null není nutné položka. Chcete-li vyhledávání záznamů rychleji pomocí pole, můžete definovat index pro pole. Je-li povolit položky Null v indexovaného pole a očekávají mnoho položek na hodnotu Null, můžete nastavit vlastnost u objektu indexu na hodnotu TRUE a snížit množství místa, které používá index. Nastavení vlastnosti Ignorovat hodnoty Null a nastavení požadovaná vlastnost společně určují, zda má záznam s hodnotou Null index položka, jak ukazuje následující tabulka.

|Ignorovat hodnoty Null|Požadováno|Index pole s hodnotou Null|
|-----------------|--------------|-------------------------|
|Hodnota TRUE|False|Hodnota Null, které jsou povoleny. žádná položka indexu s přidána.|
|False|False|Hodnota Null, které jsou povoleny. Index položky přidány.|
|True nebo False|Hodnota TRUE|Hodnota Null není povolena; žádná položka indexu s přidána.|

Další informace naleznete v tématu "Vlastnost" v nápovědě k DAO.

*m_bRequired*<br/>
Určuje, zda objekt DAO indexu vyžaduje nenulovou hodnotu. Pokud je tato vlastnost hodnotu TRUE, index objektu neumožňuje hodnotu Null. Další informace naleznete v tématu "Vyžaduje vlastnost" v nápovědě k DAO.

> [!TIP]
> Když nastavíte tuto vlastnost pro objekt index rozhraní DAO nebo objektu pole (obsažené tabledef, záznamů nebo objektu querydef), nastavit ji pro objekt, pole. Před inicializací objektu indexu se kontroluje platnost nastavení vlastností pro objekt typu pole.

*m_bForeign*<br/>
Určuje, zda objekt index představuje cizího klíče v tabulce. Pokud je tato vlastnost hodnotu TRUE, představuje index cizího klíče v tabulce. Cizí klíč se skládá z jednoho nebo více polí v tabulce cizího, které jedinečně identifikují řádek v primární tabulce. Databázový stroj Microsoft Jet vytvoří objekt indexu pro tabulku cizího a nastaví vlastnost cizího, když vytvoříte vztah, který vynucuje referenční integritu. Další informace naleznete v tématu "Cizí vlastnost" v nápovědě k DAO.

*m_lDistinctCount*<br/>
Označuje počet jedinečných u objektu indexu, které jsou zahrnuty v související tabulce. Zkontrolujte vlastnost DistinctCount a zjistit počet jedinečných hodnot nebo klíče v indexu. Libovolná klávesa se bude počítat jenom jednou, i když může mít více výskytů typů tato hodnota povoluje duplicitní hodnoty indexu. Tyto informace jsou užitečné v aplikacích, které se pokouší o přístup k datům optimalizovat vyhodnocením index informace. Počet jedinečných hodnot, který se také nazývá Kardinalita objektu indexu. Vlastnost DistinctCount nebude v určitou dobu vždy odráží skutečný počet klíčů. Například změna způsobené odvolání transakce se neprojeví okamžitě ve vlastnosti DistinctCount. Další informace naleznete v tématu "DistinctCount vlastnost" v nápovědě k DAO.

## <a name="remarks"></a>Poznámky

Odkazy na primární, sekundární a všechny výše určit, jak vrácené informace `GetIndexInfo` členskou funkci třídy [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md#getindexinfo) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Index objekty nejsou reprezentovány třídy knihovny MFC. Místo toho rozhraní DAO objekty základní objekty třídy knihovny MFC [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obsahovat kolekce objektů index, volá kolekci indexů. Tyto třídy zadat členské funkce pro přístup k jednotlivým položkám index informace nebo je všechny najednou se dostanete `CDaoIndexInfo` objektu voláním `GetIndexInfo` členské funkce nadřazeného objektu.

`CDaoIndexInfo` má konstruktor a destruktor, aby bylo možné správně přidělit a uvolnit informace indexu pole v `m_pFieldInfos`.

Načte informace `GetIndexInfo` členské funkce objektu tabledef je uložen v `CDaoIndexInfo` struktury. Volání `GetIndexInfo` členskou funkci obsahujícího objektu tabledef, v jejichž indexy kolekci index objekt se uloží. `CDaoIndexInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoIndexInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
