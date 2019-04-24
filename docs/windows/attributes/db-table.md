---
title: db_table (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 3ab548261d6ebcb9d3d7f7e352c8afe3b33db06f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148117"
---
# <a name="dbtable"></a>db_table

Otevře se tabulku OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

#### <a name="parameters"></a>Parametry

*db_table*<br/>
Řetězec určující název databázové tabulky (například "produktů").

*Jméno*<br/>
(Volitelné) Název popisovače, který slouží pro práci s tabulkou. Tento parametr musíte zadat, pokud se chcete vrátit více než jeden řádek výsledků. **db_table** generuje proměnné se zadaným *název* , který slouží k procházení řádků nebo spustit více dotazů akce.

*source_name*<br/>
(Volitelné) `CSession` Proměnnou nebo instance třídy, která má `db_source` atribut WebMethod na kterém příkaz spustí. Zobrazit [db_source](db-source.md).

*Hodnota HRESULT*<br/>
(Volitelné) Určuje proměnné, která se zobrazí hodnota HRESULT tohoto databázového příkazu. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.

## <a name="remarks"></a>Poznámky

**db_table** vytvoří [CTable](../../data/oledb/ctable-class.md) objekt, který používá příjemce technologie OLE DB otevřít tabulku. Tento atribut lze použít pouze na úrovni třídy; nelze ji použít vložený. Použít `db_column` proměnných, vytvořit vazbu sloupců tabulky použijte `db_param` pro vymezení (nastavený typ parametru a to v) parametrů.

Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.

## <a name="example"></a>Příklad

Následující příklad otevře tabulky produktů pro použití u `CProducts`.

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

Příklad tohoto atributu použijí v aplikaci, najdete v ukázkách [AtlAgent](https://github.com/Microsoft/VCSamples) a [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)
