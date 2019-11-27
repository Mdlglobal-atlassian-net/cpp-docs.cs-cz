---
title: CDaoFieldInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: e2638ac908e4e286530301bc913173e87008df47
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303697"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo – struktura

Struktura `CDaoFieldInfo` obsahuje informace o objektu pole definovaném pro objekty DAO (Data Access Object).

Rozhraní DAO je podporováno prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

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
Jedinečný název objektu pole. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost názvu".

*m_nType*<br/>
Hodnota, která určuje datový typ pole. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost typu". Hodnota této vlastnosti může být jedna z následujících:

- `dbBoolean` ano/ne, stejné jako TRUE/FALSE

- `dbByte` bajt

- `dbInteger` krátký

- `dbLong` Long

- `dbCurrency` měna; Viz MFC Class [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` Single

- `dbDouble` Double

- `dbDate` datum/čas; Viz MFC Class [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` text; Viz MFC Class [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Long Binary (objekt OLE); můžete chtít použít knihovnu MFC Class [CByteArray](../../mfc/reference/cbytearray-class.md) namísto třídy `CLongBinary`, protože `CByteArray` je bohatší a snadněji se používá.

- `dbMemo`ý zápis; Viz MFC Class `CString`

- `dbGUID` globálně jedinečný identifikátor nebo univerzálně jedinečný identifikátor, který se používá u vzdálených volání procedur. Další informace naleznete v nápovědě k rozhraní DAO v tématu "vlastnost typu".

> [!NOTE]
>  Nepoužívejte řetězcové datové typy pro binární data. To způsobí, že vaše data budou probíhat prostřednictvím vrstvy překladu Unicode/ANSI, což vede k větší režii a pravděpodobně neočekávanému překladu.

*m_lSize*<br/>
Hodnota, která určuje maximální velikost objektu pole DAO (v bajtech), který obsahuje text nebo pevnou velikost objektu pole, který obsahuje textové nebo číselné hodnoty. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost velikosti". Velikost může být jedna z následujících hodnot:

|Typ|Velikost (bajty)|Popis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Ano/ne (totéž jako true/false)|
|`dbByte`|1|Bajt|
|`dbInteger`|2|Celé číslo|
|`dbLong`|4|Dlouhé|
|`dbCurrency`|8|Měna ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Jednoduché|
|`dbDouble`|8|Double|
|`dbDate`|8|Datum a čas ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objekt OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); použít místo `CLongBinary`)|
|`dbMemo`|0|Memo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Globálně jedinečný identifikátor/univerzálně jedinečný identifikátor, který se používá u vzdálených volání procedur.|

*m_lAttributes*<br/>
Určuje vlastnosti objektu pole obsaženého v objektu tabledef, Recordset, querydef nebo index. Vrácená hodnota může být součet těchto konstant vytvořená pomocí operátoru C++ bitového operátoru OR ( **&#124;** ):

- `dbFixedField` je velikost pole Pevná (výchozí pro číselná pole).

- `dbVariableField` velikost pole je proměnná (pouze textová pole).

- `dbAutoIncrField` hodnota pole pro nové záznamy se automaticky zvýší na jedinečné dlouhé celé číslo, které nelze změnit. Podporováno pouze pro databázové tabulky Microsoft Jet.

- `dbUpdatableField` hodnotu pole lze změnit.

- `dbDescending` pole je seřazeno sestupně (Z-A nebo 100-0) pořadí (platí pouze pro objekt pole v kolekci pole objektu index; v knihovně MFC jsou objekty indexu samy obsaženy v objektech tabledef). Pokud tuto konstantu vynecháte, pole se seřadí ve vzestupném pořadí (A-Z nebo 0-100) (výchozí).

Při kontrole nastavení této vlastnosti můžete použít C++ BITOVÝ operátor and ( **&** ) k otestování konkrétního atributu. Při nastavování více atributů je lze kombinovat kombinací příslušných konstant s operátorem bitového operátoru OR **&#124;** (). Podrobnosti najdete v tématu "vlastnosti atributů" v nápovědě k rozhraní DAO.

*m_nOrdinalPosition*<br/>
Hodnota, která určuje číselné pořadí, ve kterém chcete, aby se pole reprezentované objektem pole DAO zobrazilo relativně k jiným polím. Tuto vlastnost lze nastavit pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Podrobnosti najdete v tématu "vlastnost OrdinalPosition" v nápovědě k rozhraní DAO.

*m_bRequired*<br/>
Označuje, zda objekt pole DAO vyžaduje hodnotu, která není null. Pokud má tato vlastnost hodnotu TRUE, pole nepovoluje hodnotu null. Pokud je parametr Required nastaven na hodnotu FALSE, může pole obsahovat hodnoty null a také hodnoty, které splňují podmínky zadané v nastavení vlastnosti povolit a zadat ověřovací pravidlo. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "požadovaná vlastnost". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Označuje, zda je prázdný řetězec ("") platnou hodnotou objektu pole DAO s datovým typem text nebo Memo. Pokud má tato vlastnost hodnotu TRUE, prázdný řetězec je platná hodnota. Tuto vlastnost lze nastavit na hodnotu FALSE, aby bylo zajištěno, že nelze použít prázdný řetězec k nastavení hodnoty pole. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost s nulovou vlastností". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Určuje pořadí řazení v textu pro porovnání a řazení řetězců. Podrobnosti najdete v tématu Přizpůsobení nastavení registru Windows pro přístup k datům v nápovědě k rozhraním DAO. Seznam možných vrácených hodnot naleznete v tématu `m_lCollatingOrder` člen struktury [CDaoDatabaseInfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) . Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Hodnota, která v relaci Určuje název objektu pole DAO v cizí tabulce, který odpovídá poli v primární tabulce. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost cizího pole".

*m_strSourceField*<br/>
Určuje název pole, které je původním zdrojem dat pro objekt pole DAO obsažený v objektu tabledef, Recordset nebo querydef. Tato vlastnost označuje původní název pole přidružený k objektu pole. Pomocí této vlastnosti můžete například určit původní zdroj dat v poli dotazu, jehož název nesouvisí s názvem pole v podkladové tabulce. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "SourceField a vlastnosti zdroje". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Určuje název tabulky, která je původním zdrojem dat pro objekt pole DAO obsažený v objektu tabledef, Recordset nebo querydef. Tato vlastnost označuje původní název tabulky přidružený k objektu pole. Pomocí této vlastnosti můžete například určit původní zdroj dat v poli dotazu, jehož název nesouvisí s názvem pole v podkladové tabulce. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "SourceField a vlastnosti zdroje". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Hodnota, která ověřuje data v poli, jak je změněno nebo přidáno do tabulky. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost ověřovací pravidlo". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Související informace o TableDefs naleznete v tématu `m_strValidationRule` člen struktury [CDaoTableDefInfo –](../../mfc/reference/cdaotabledefinfo-structure.md) .

*m_strValidationText*<br/>
Hodnota, která určuje text zprávy, kterou aplikace zobrazuje, pokud hodnota objektu pole DAO nevyhovuje ověřovacímu pravidlu, které je určeno nastavením vlastnosti ověřovací pravidlo. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost ověřovacího hesla". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Výchozí hodnota objektu pole DAO. Při vytvoření nového záznamu se automaticky zadá nastavení vlastnosti DefaultValue jako hodnota pro pole. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost DefaultValue". Tuto vlastnost můžete nastavit pro tabledef pomocí [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Poznámky

Odkazy na primární, sekundární a všechny výše označují, jak jsou vráceny informace funkcí `GetFieldInfo` členské funkce ve třídách [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Objekty pole nejsou reprezentovány třídou MFC. Místo toho objekty DAO podkladové objekty MFC následujících tříd obsahují kolekce objektů polí: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)a [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Tyto třídy poskytují členské funkce pro přístup k některým položkám informací o poli nebo k nim můžete přistupovat pomocí objektu `CDaoFieldInfo` voláním členské funkce `GetFieldInfo` objektu, který jej obsahuje.

Kromě jejího použití pro zkoumání vlastností objektu můžete také použít `CDaoFieldInfo` k vytvoření vstupního parametru pro vytváření nových polí v tabledef. Pro tuto úlohu jsou k dispozici jednodušší možnosti, ale pokud chcete přesnější řízení, můžete použít verzi [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) , která přebírá parametr `CDaoFieldInfo`.

Informace načtené členskou funkcí `GetFieldInfo` (třídy obsahující pole) jsou uložené ve `CDaoFieldInfo` struktuře. Zavolejte členskou funkci `GetFieldInfo` nadřazeného objektu, ve kterém je uložena kolekce polí objekt pole. `CDaoFieldInfo` také definuje členskou funkci `Dump` v sestaveních ladění. K výpisu obsahu `CDaoFieldInfo` objektu můžete použít `Dump`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef:: GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset:: GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef:: GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
