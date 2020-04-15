---
title: CDaoFieldInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368401"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo – struktura

Struktura `CDaoFieldInfo` obsahuje informace o objektu pole definovaném pro objekty přístupu k datům (DAO).

DAO je podporováno prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé.

## <a name="syntax"></a>Syntaxe

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Jednoznačně pojmenuje objekt pole. Podrobnosti naleznete v tématu "Name Property" v nápovědě dao.

*m_nType*<br/>
Hodnota, která označuje datový typ pole. Podrobnosti naleznete v tématu "Type Property" v nápovědě dao. Hodnota této vlastnosti může být jedna z následujících:

- `dbBoolean`Ano/Ne, stejné jako PRAVDA/NEPRAVDA

- `dbByte`Bajt

- `dbInteger`Krátké

- `dbLong`Dlouhé

- `dbCurrency`Měna; viz Třída MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`Jednoho

- `dbDouble`Dvojité

- `dbDate`Datum a čas; viz Třída MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`Text; viz MFC třídy [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`Dlouhý binární (objekt OLE); můžete chtít použít třídu MFC [CByteArray](../../mfc/reference/cbytearray-class.md) místo třídy, `CLongBinary` protože `CByteArray` je bohatší a snadněji použitelné.

- `dbMemo`Poznámka; viz třída MFC`CString`

- `dbGUID`Globálně jedinečný identifikátor/univerzálně jedinečný identifikátor používaný při vzdálených voláních procedur. Další informace naleznete v tématu "Type Property" v nápovědě dao.

> [!NOTE]
> Nepoužívejte datové typy řetězce pro binární data. To způsobí, že vaše data projít vrstvy překladu Unicode/ANSI, výsledkem zvýšené režie a možná neočekávaný překlad.

*m_lSize*<br/>
Hodnota, která označuje maximální velikost objektu pole DAO v bajtech, který obsahuje text nebo pevnou velikost objektu pole, který obsahuje textové nebo číselné hodnoty. Podrobnosti naleznete v tématu "Vlastnost velikosti" v nápovědě dao. Velikosti mohou být jednu z následujících hodnot:

|Typ|Velikost (bajty)|Popis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Ano/Ne (stejné jako pravda/nepravda)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Integer|
|`dbLong`|4|Dlouhé|
|`dbCurrency`|8|Měna ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Datum a čas ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Dlouhý binární (objekt OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); místo ) `CLongBinary`|
|`dbMemo`|0|Poznámka ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Globálně jedinečný identifikátor/univerzálně jedinečný identifikátor používaný při vzdálených voláních procedur.|

*m_lAttributes*<br/>
Určuje charakteristiky objektu pole obsaženého v objektu tabledef, recordset, querydef nebo indexu. Vrácená hodnota může být součtem těchto konstant vytvořených pomocí operátoru C++ bitwise-OR (**&#124;): **

- `dbFixedField`Velikost pole je pevná (výchozí pro číselná pole).

- `dbVariableField`Velikost pole je proměnná (pouze textová pole).

- `dbAutoIncrField`Hodnota pole pro nové záznamy se automaticky zintáží na jedinečné dlouhé celé číslo, které nelze změnit. Podporováno pouze pro databázové tabulky Microsoft Jet.

- `dbUpdatableField`Hodnotu pole lze změnit.

- `dbDescending`Pole je seřazeno v sestupném pořadí (Z - A nebo 100 - 0) (vztahuje se pouze na objekt pole v kolekci Polí objektu indexu; v knihovně MFC jsou objekty indexu samy obsaženy v objektech tabledef). Pokud tuto konstantu vynechete, pole seřadí vzestupně (A - Z nebo 0 - 100) (výchozí).

Při kontrole nastavení této vlastnosti můžete použít operátor C++ bitwise-AND (**&**) k testování konkrétního atributu. Při nastavování více atributů je můžete kombinovat kombinací příslušných konstant s operátorem BITWISE-OR (**&#124;). ** Podrobnosti naleznete v tématu "Vlastnost atributů" v nápovědě dao.

*m_nOrdinalPosition*<br/>
Hodnota, která určuje číselné pořadí, ve kterém má být zobrazeno pole reprezentované objektem pole DAO vzhledem k ostatním polím. Tuto vlastnost můžete nastavit pomocí [cdaotabledef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Podrobnosti naleznete v tématu "OrdinalPosition Property" v nápovědě DAO.

*m_bRequired*<br/>
Označuje, zda objekt pole DAO vyžaduje hodnotu nenulové. Pokud je tato vlastnost TRUE, pole neumožňuje hodnotu Null. Pokud je hodnota Required nastavena na hodnotu NEPRAVDA, může pole obsahovat hodnoty Null a hodnoty, které splňují podmínky určené nastavením vlastností AllowZeroLength a ValidationRule. Podrobnosti naleznete v tématu "Povinné zařízení" v nápovědě dao. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Označuje, zda je prázdný řetězec ("") platnou hodnotou objektu pole DAO s datovým typem Text nebo Memo. Pokud je tato vlastnost TRUE, prázdný řetězec je platná hodnota. Tuto vlastnost můžete nastavit na HODNOTU NEPRAVDA, abyste zajistili, že k nastavení hodnoty pole nelze použít prázdný řetězec. Podrobnosti naleznete v tématu "AllowZeroLength Property" v nápovědě DAO. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Určuje pořadí řazení v textu pro porovnání řetězců nebo řazení. Podrobnosti naleznete v tématu "Přizpůsobení nastavení registru systému Windows pro přístup k datům" v nápovědě dao. Seznam možných vrácených hodnot naleznete `m_lCollatingOrder` v členu struktury [CDaoDatabaseInfo.](../../mfc/reference/cdaodatabaseinfo-structure.md) Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Hodnota, která v relaci určuje název objektu pole DAO v cizí tabulce, který odpovídá poli v primární tabulce. Podrobnosti naleznete v tématu "ForeignName Property" v nápovědě DAO.

*m_strSourceField*<br/>
Označuje název pole, které je původním zdrojem dat pro objekt pole DAO obsažený v objektu tabledef, recordset nebo querydef. Tato vlastnost označuje původní název pole přidružený k objektu pole. Tuto vlastnost můžete například použít k určení původního zdroje dat v poli dotazu, jehož název nesouvisí s názvem pole v podkladové tabulce. Podrobnosti naleznete v tématu "SourceField, SourceTable Properties" v nápovědě DAO. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Označuje název tabulky, která je původním zdrojem dat pro objekt pole DAO obsažený v objektu tabledef, recordset nebo querydef. Tato vlastnost označuje původní název tabulky přidružený k objektu pole. Tuto vlastnost můžete například použít k určení původního zdroje dat v poli dotazu, jehož název nesouvisí s názvem pole v podkladové tabulce. Podrobnosti naleznete v tématu "SourceField, SourceTable Properties" v nápovědě DAO. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Hodnota, která ověřuje data v poli při změně nebo přidání do tabulky. Podrobnosti naleznete v tématu "ValidationRule Property" v nápovědě DAO. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Související informace o tabledefs `m_strValidationRule` naleznete v člen [cdaotableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) struktury.

*m_strValidationText*<br/>
Hodnota, která určuje text zprávy, která se zobrazí v aplikaci, pokud hodnota objektu pole DAO nesplňuje ověřovací pravidlo určené nastavením vlastnosti ValidationRule. Podrobnosti naleznete v tématu "Vlastnost ValidationText" v nápovědě DAO. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Výchozí hodnota objektu pole DAO. Při vytvoření nového záznamu se automaticky zadá jako hodnota pole nastavení vlastnosti DefaultValue. Podrobnosti naleznete v tématu "DefaultValue Property" v nápovědě DAO. Tuto vlastnost můžete nastavit pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Poznámky

Odkazy na primární, sekundární a všechny výše označují, jak `GetFieldInfo` jsou informace vráceny členskou funkcí ve třídách [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Objekty pole nejsou reprezentovány třídou knihovny MFC. Místo toho objekty DAO základní objekty knihovny MFC následujících tříd obsahují kolekce objektů pole: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)a [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Tyto třídy poskytují členské funkce pro přístup k některým jednotlivým položkám `CDaoFieldInfo` informací o `GetFieldInfo` poli, nebo k nim můžete přistupovat všechny najednou pomocí objektu voláním členské funkce obsahujícího objektu.

Kromě jeho použití pro zkoumání vlastností `CDaoFieldInfo` objektu můžete také vytvořit vstupní parametr pro vytváření nových polí v tabledef. Pro tento úkol jsou k dispozici jednodušší možnosti, ale pokud chcete jemnější řízení, můžete použít verzi `CDaoFieldInfo` [CDaoTableDef::CreateField,](../../mfc/reference/cdaotabledef-class.md#createfield) která přebírá parametr.

Informace načtené `GetFieldInfo` členovou funkcí (třídy, která obsahuje pole) jsou uloženy ve `CDaoFieldInfo` struktuře. Volání `GetFieldInfo` členské funkce obsahující objekt, ve jehož Fields kolekce objektu pole je uložen. `CDaoFieldInfo`také definuje `Dump` členská funkce v sestavení ladění. Můžete použít `Dump` k výpisu `CDaoFieldInfo` obsahu objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[Sada záznamů CDao::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
