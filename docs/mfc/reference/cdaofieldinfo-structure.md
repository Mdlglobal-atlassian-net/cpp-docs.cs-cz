---
title: Cdaofieldinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaf3f41bf6a6fe5d67ec5835d57889f6ec7dbae6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437679"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo – struktura

`CDaoFieldInfo` Struktura obsahuje informace o objektu pole definovány pro datový přístup k objektům (DAO).

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
Pole objektu jedinečné názvy. Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_nType*<br/>
Hodnota, která určuje datový typ pole. Podrobnosti naleznete v tématu "Vlastnost typu" v nápovědě k DAO. Hodnota této vlastnosti může být jedna z následujících akcí:

- `dbBoolean` Ano/Ne stejně jako TRUE nebo FALSE

- `dbByte` Bajtů

- `dbInteger` krátké

- `dbLong` Long

- `dbCurrency` Měně. Třída knihovny MFC naleznete v tématu [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` Jeden

- `dbDouble` Double

- `dbDate` Datum a čas; Třída knihovny MFC naleznete v tématu [COleDateTime –](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` Text. Třída knihovny MFC naleznete v tématu [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Dlouhá binární soubor (objekt OLE); můžete chtít použít třídy MFC [CByteArray](../../mfc/reference/cbytearray-class.md) namísto třídy `CLongBinary` jako `CByteArray` bohatší a usnadňuje používání.

- `dbMemo` Úloh. Třída knihovny MFC naleznete v tématu `CString`

- `dbGUID` Globálně jedinečný identifikátor/univerzálně jedinečný identifikátor využít vzdálené volání procedur. Další informace naleznete v tématu "Vlastnost typu" v nápovědě k DAO.

> [!NOTE]
>  Nepoužívejte řetězcovými datovými typy pro binární data. To způsobí, že vaše data předávání transakční vrstva Unicode/ANSI, což vede k vyšší nároky a může být neočekávané překlad.

*m_lSize*<br/>
Hodnota, která určuje maximální velikost v bajtech DAO pole objektu, který obsahuje text nebo pevné velikosti pole objektu, který obsahuje textové nebo číselné hodnoty. Podrobnosti naleznete v tématu "Vlastnost Size" v nápovědě k DAO. Velikosti může být jedna z následujících hodnot:

|Typ|Velikost (bajty)|Popis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Ano/Ne (stejné jako True/False)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Integer|
|`dbLong`|4|Long|
|`dbCurrency`|8|Měny ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Datum a čas ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Dlouhá binární soubor (OLE Object; [CByteArray](../../mfc/reference/cbytearray-class.md); použijte místo `CLongBinary`)|
|`dbMemo`|0|Memo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Globálně jedinečný identifikátor/univerzálně jedinečný identifikátor využít vzdálené volání procedur.|

*m_lAttributes*<br/>
Určuje vlastnosti pole objektů obsažených tabledef, sady záznamů, querydef nebo objekt indexu. Vrácená hodnota může být součet těchto konstanty, vytvořené pomocí jazyka C++ bitového operátoru OR (**&#124;**) – operátor:

- `dbFixedField` Velikost pole je pevně (výchozí nastavení pro číselné pole).

- `dbVariableField` Velikost pole je proměnná (pouze textové pole).

- `dbAutoIncrField` Hodnotu pole pro nové záznamy se automaticky zvýší na jedinečné long integer, která se nedá změnit. Podporováno pouze pro Microsoft Jet databázových tabulek.

- `dbUpdatableField` Můžete změnit hodnotu pole.

- `dbDescending` Pole je seřazen v sestupném (Z - A nebo 100-0) pořadí (platí pouze pro pole objektů v kolekci polí indexu objektu; v knihovně MFC, index samotné objekty jsou obsažené v objektech tabledef). Vynecháte-li tato konstanta, pole je seřazen vzestupně (A – Z nebo 0 – 100) pořadí (výchozí).

Při kontrole nastavení této vlastnosti můžete použít C++ bitový – a – operátor (**&**) k testování pro konkrétní atribut. Při nastavování více atributů, můžete je spojit kombinací odpovídající konstanty bitového operátoru OR (**&#124;**) – operátor. Podrobnosti naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

*m_nOrdinalPosition*<br/>
Hodnota, která určuje číselného pořadí, ve kterém má být pole reprezentována objekt pole DAO zobrazeného vzhledem k jiné pole. Můžete nastavit tuto vlastnost s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Podrobnosti naleznete v tématu "OrdinalPosition vlastnost" v nápovědě k DAO.

*m_bRequired*<br/>
Určuje, zda objekt pole DAO vyžaduje nenulovou hodnotu. Pokud je tato vlastnost hodnotu TRUE, pole neumožňuje hodnotu Null. V případě potřeby je nastavena na hodnotu FALSE, pole může obsahovat hodnoty Null, stejně jako hodnoty, které splňují podmínky určené nastavení vlastností nulovou a ověřovací pravidlo. Podrobnosti naleznete v tématu "Vyžaduje vlastnost" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Označuje, zda prázdný řetězec ("") je platná hodnota objektu rozhraní DAO pole s datovým typem Text nebo. Pokud je tato vlastnost hodnotu TRUE, je prázdný řetězec platnou hodnotu. Tuto vlastnost můžete nastavit na FALSE, pokud chcete zajistit, že nelze použít prázdný řetězec a nastavit hodnotu pole. Podrobnosti naleznete v tématu "Nulovou vlastnost" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Určuje pořadí řazení v textu pro porovnání řetězců nebo řazením. Podrobnosti najdete v tématu "Přizpůsobení Windows registru nastavení pro přístup k datům" v nápovědě rozhraní DAO. Seznam možných hodnot vrácených najdete v tématu `m_lCollatingOrder` člena [cdaodatabaseinfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Hodnota, která v relaci, určuje název objektu pole DAO v cizím tabulku, která odpovídají polím v primární tabulce. Podrobnosti naleznete v tématu "ForeignName vlastnost" v nápovědě k DAO.

*m_strSourceField*<br/>
Určuje název pole, které je původní zdroj dat pro objekt pole DAO obsažené tabledef, záznamů nebo querydef objektu. Tato vlastnost určuje původní název pole, které jsou přidružené k objektu pole. Tato vlastnost může například použít k určení původní zdroj dat v dotazu pole, jehož název nesouvisí s názvem pole v podkladové tabulce. Podrobnosti naleznete v tématu "SourceField vlastnosti SourceTable" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Určuje název tabulky, která je původní zdroj dat pro objekt pole DAO obsažené tabledef, záznamů nebo querydef objektu. Tato vlastnost určuje původní název tabulky přidružené k objektu pole. Tato vlastnost může například použít k určení původní zdroj dat v dotazu pole, jehož název nesouvisí s názvem pole v podkladové tabulce. Podrobnosti naleznete v tématu "SourceField vlastnosti SourceTable" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Hodnota, která ověřuje data v poli jako ho se nezmění ani nepřidá do tabulky. Podrobnosti naleznete v tématu "Ověřovací pravidlo vlastnost" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Související informace o tabledefs – najdete v tématu `m_strValidationRule` člena [cdaotabledefinfo –](../../mfc/reference/cdaotabledefinfo-structure.md) struktury.

*m_strValidationText*<br/>
Hodnota, která určuje text zprávy, která vaše aplikace zobrazí, pokud hodnota objekt DAO pole nevyhovuje zadané nastavením vlastnosti Ověřovací pravidlo ověřování. Podrobnosti naleznete v tématu "Ověřovací vlastnost" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Výchozí hodnota objektu pole DAO. Když se vytvoří nový záznam, nastavení vlastnosti DefaultValue se vyplní automaticky jako hodnotu pro pole. Podrobnosti naleznete v tématu "Výchozí hodnota vlastnosti" v nápovědě k DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Poznámky

Odkazy na primární, sekundární a všechny výše určit, jak vrácené informace `GetFieldInfo` členskou funkci třídy [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), a [ CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Pole objektů nejsou reprezentovány třídy knihovny MFC. Místo toho základní objekty následující třídy knihovny MFC rozhraní DAO objekty obsahují kolekce pole objektů: [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), a [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md). Tyto třídy zadat členské funkce pro přístup k některé jednotlivých položek informací o poli, nebo je všechny najednou se dostanete `CDaoFieldInfo` objektu voláním `GetFieldInfo` členské funkce nadřazeného objektu.

Kromě jeho použití pro zkoumání vlastností objektu můžete také použít `CDaoFieldInfo` vytvořit vstupní parametr pro vytvoření nových polí v tabledef. Jednodušší možnosti jsou k dispozici pro tuto úlohu, ale pokud chcete lepší kontrolu, můžete použít verzi [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) , která přijímá `CDaoFieldInfo` parametru.

Načte informace `GetFieldInfo` členská funkce (třídy, která obsahuje pole) je uložen v `CDaoFieldInfo` struktury. Volání `GetFieldInfo` obsahujícího objektu, v jehož kolekce polí objekt pole je uložen v členské funkci. `CDaoFieldInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoFieldInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)

