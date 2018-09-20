---
title: 'TN002: Formát dat trvalých objektů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a23ade068fa0d71715a76d3a99a393cc5458947c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399961"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formát dat trvalých objektů

Tato poznámka popisuje rutiny knihovny MFC, které podporují trvalé objekty C++ a formát data objektu, když je uložena v souboru. To platí pouze pro třídy s [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) makra.

## <a name="the-problem"></a>Problém

Implementace MFC pro trvalá data ukládá data pro mnoho objektů v jedné souvislé části souboru. Objektu `Serialize` metoda převádí data objektu na kompaktní binární formát.

Implementace zaručuje, že se všechna data uložena ve stejném formátu pomocí [CArchive – třída](../mfc/reference/carchive-class.md). Použije `CArchive` objektu jako převaděče. Tento objekt nevyřeší od doby, kdy se vytvoří až do okamžiku volání [CArchive::Close](../mfc/reference/carchive-class.md#close). Tuto metodu lze volat buď programátorem výslovně nebo implicitně destruktor při ukončení programu, který obsahuje obor `CArchive`.

Tato poznámka popisuje provádění `CArchive` členy [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) a [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Najdete kód pro tyto funkce v Arcobj.cpp a hlavní implementace `CArchive` v Arccore.cpp. Uživatelský kód nevolá `ReadObject` a `WriteObject` přímo. Místo toho používají tyto objekty specifický pro třídu typově bezpečné vložení a extrakci operátory, které jsou automaticky generovány DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Následující kód ukazuje, jak `WriteObject` a `ReadObject` jsou implicitně volána:

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Ukládání objektů pro Store (CArchive::WriteObject)

Metoda `CArchive::WriteObject` zapíše data záhlaví, který se používá k rekonstrukci objektu. Tato data se skládá ze dvou částí: typ objektu a stav objektu. Tato metoda je také odpovědná za správu identity objektu zapisovaná, tak, aby se uloží pouze jedna kopie, bez ohledu na počet ukazatelů na tento objekt (včetně cyklické ukazatele).

Uložení (vkládání) a obnovení objektů (extrahování) závisí na několika "konstanty manifestu." Toto jsou hodnoty, které jsou uloženy v binárním souboru a důležitými informacemi do archivní úrovně (Všimněte si, že předpona "w" označuje množství 16 bitů):

|Značka|Popis|
|---------|-----------------|
|wNullTag|Používá se pro objekt ukazatele NULL (0).|
|wNewClassTag|Označuje, že je nový kontext archivu (-1) popis třídy, který následuje.|
|wOldClassTag|Označuje, že třídu objektu, který je čten ukázala v tomto kontextu (0x8000).|

Při ukládání objektů, archivu udržuje [cmapptrtoptr –](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*) která je mapování z uložený objekt na trvalý identifikátor 32-bit (PID). Identifikátor PID je přiřazen do všech jedinečných objektů a každý jedinečný název třídy, který je uložen v rámci archivu. Tyto PID je předat službě postupně počínaje 1. Tyto PID nemají žádný význam mimo obor archivu a především se by se zaměňovat s záznam čísla nebo jiné položky identity.

V `CArchive` třídy, PID jsou 32-bit, ale jsou pokud jsou větší než 0x7FFE zapsány jako 16bitové navýšení kapacity. Velké PID se zapisují jako 0x7FFF, za nímž následuje identifikátor PID 32-bit. Tím se zachová kompatibilitu s projekty, které byly vytvořeny v dřívějších verzích.

Po odeslání žádosti se uložit objekt do archivu (obvykle pomocí operátoru globální vložení) s hodnotou Null se provede kontrola [CObject](../mfc/reference/cobject-class.md) ukazatele. Jestliže je ukazatel NULL, *wNullTag* je vložen do archivní datový proud.

Pokud ukazatel není NULL a lze serializovat (třída je `DECLARE_SERIAL` třídy), kontroly kódu *m_pStoreMap* chcete zobrazit, zda byl objekt již uložen. Pokud ano, vloží kód PID 32-bit spojený s tímto objektem do archivní datový proud.

Pokud objekt nebyl uložen před, existují dvě možnosti, které byste měli zvážit: objekt a přesného typu objektu (třídy) jsou nové pro tento kontext archivu nebo objekt je typu přesné už jednou vyskytl. K určení, zda typ ukázala, kód dotazy *m_pStoreMap* pro [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objekt, který odpovídá `CRuntimeClass` objekt přidružený k objektu se ukládá. Pokud není nalezena shoda, `WriteObject` vloží značku, která je bitového `OR` z *wOldClassTag* a tento index. Pokud `CRuntimeClass` je nový kontext archivu `WriteObject` přiřadí nový identifikátor PID pro danou třídu a vloží jej do archivu předcházet párový příkaz *wNewClassTag* hodnotu.

Popisovač pro tuto třídu se pak vloží do archivu pomocí `CRuntimeClass::Store` metody. `CRuntimeClass::Store` Vloží číslo schéma třídy (viz níže) a ASCII textový název třídy. Všimněte si, že použití názvu text ASCII nezaručuje jedinečnost archivu napříč aplikacemi. Proto by mělo být označení vašich datových souborů, abyste zabránili poškození. Po vložení informací o třídě archivu umístí do objektu *m_pStoreMap* a pak zavolá `Serialize` metoda k vložení dat specifický pro třídu. Umístit do objektu *m_pStoreMap* před voláním `Serialize` brání více kopií daného objektu, neuloží se do storu.

Při návratu do počáteční volající (obvykle kořenové síťových objektů), je nutné volat [CArchive::Close](../mfc/reference/carchive-class.md#close). Pokud budete chtít provést další [cfile –](../mfc/reference/cfile-class.md)operace, je třeba zavolat `CArchive` metoda [vyprázdnění](../mfc/reference/carchive-class.md#flush) zabránit poškození archivu.

> [!NOTE]
>  Tato implementace má vynucené omezení 0x3FFFFFFE indexů archivu kontextu. Toto číslo představuje maximální počet jedinečných objektů a třídy, které lze uložit do jednoho archivu, ale jeden disk soubor může obsahovat neomezený počet kontextů archivu.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Načítání objektů z Store (CArchive::ReadObject)

Načítají se (extrahování) používá objekty `CArchive::ReadObject` metody a je první z `WriteObject`. Stejně jako u `WriteObject`, `ReadObject` nevolá přímo v uživatelském kódu; uživatelský kód by měly volat operátor extrakce zajišťující bezpečnost typů, která volá `ReadObject` s očekávané `CRuntimeClass`. Díky integrity typ operace extrakce.

Protože `WriteObject` implementace přiřazené rostoucí PID a začínají hodnotou 1 (0 je předdefinovaná jako objekt NULL), `ReadObject` implementace můžete použít pole pro uchování stavu archivu kontextu. Když identifikátor PID je pro čtení z úložiště, pokud identifikátor PID je větší než aktuální horní mez *m_pLoadArray*, `ReadObject` ví, že následuje nový objekt (nebo popisu třídy).

## <a name="schema-numbers"></a>Schéma čísla

Číslo schématu, které je přiřazeno k třídě při `IMPLEMENT_SERIAL` metoda třídy dochází, je "verze" implementace třídy. Schéma označuje implementaci třídy, aby počet, kolikrát daný objekt byl proveden trvalé (obvykle označované jako verze objektu).

Pokud máte v úmyslu spravovat několik různých implementací stejné třídy v čase, zvyšování schématu, jak zkontrolovat svůj objekt `Serialize` implementace metody vám umožňuje napsat kód, který lze načíst objekty uložené pomocí starší verze implementace.

`CArchive::ReadObject` Vyvolá metoda výjimku [carchiveexception –](../mfc/reference/carchiveexception-class.md) Pokud nalezne číslo schématu v trvalé úložiště, které se liší od počtu schéma popisu třídy v paměti. Není snadné zotavení z této výjimky.

Můžete použít `VERSIONABLE_SCHEMA` v kombinaci s (bitový **nebo**) verzi schématu zachovat vyvolání této výjimky. S použitím `VERSIONABLE_SCHEMA`, váš kód může přijmout vhodná opatření jeho `Serialize` funkce tak, že zkontrolujete návratovou hodnotu z [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Volání serializovat přímo

V mnoha případech režii schématu archivu obecný objekt `WriteObject` a `ReadObject` není nutné. To je běžné serializace dat do [CDocument](../mfc/reference/cdocument-class.md). V takovém případě `Serialize` metodu `CDocument` je volat přímo, ne s operátory extrahovat nebo insert. Obsah dokumentu zase používat obecnější režim archivu objektu.

Volání `Serialize` přímo má následující výhody a nevýhody:

- Žádné další bajty jsou přidány do archivní úrovně před nebo po je objekt serializován. To nejen umožňuje uložených dat menší, ale umožňuje implementovat `Serialize` rutin, které dokáže zpracovat všechny formáty souborů.

- Knihovny MFC je vyladěný proto `WriteObject` a `ReadObject` implementace a souvisejících kolekcích nebude propojena do vaší aplikace, pokud nepotřebujete obecnější režim objekt archivu pro některé jiné účely.

- Váš kód nebude muset obnovit ze staré čísla schématu. Díky tomu váš kód serializace dokumentu za kódování schématu čísla, čísla verzí souboru formátu nebo libovolné identifikace čísla pomocí na začátku datové soubory.

- Libovolný objekt, který je serializované pomocí přímého volání `Serialize` nesmí používat `CArchive::GetObjectSchema` nebo musí popisovač návratovou hodnotu -1 (UINT) označující, že na verzi nebyl známý.

Protože `Serialize` je volána přímo na váš dokument není obvykle možné pro dílčí objekty dokumentu k archivaci odkazy na jejich nadřazené dokumentu. Tyto objekty musí být dán ukazatel jejich dokumentu kontejneru explicitně nebo je nutné použít [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) funkce pro mapování `CDocument` ukazatel na identifikátor PID předtím, než jsou archivovány tyto back ukazatele.

Jak bylo uvedeno dříve, měli byste kódování verze a třídy informací, sami při volání `Serialize` přímo, takže umožňuje později změnit ve formátu a přitom zachovávat zpětné kompatibility se starším soubory. `CArchive::SerializeClass` Funkce lze explicitně volat před přímo serializace objektu nebo před voláním metody základní třídy.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

