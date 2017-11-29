---
title: '&lt;FileSystem&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
dev_langs: C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: b6e6523b197be2b55847f23447a6d832f55e880d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltfilesystemgt-functions"></a>&lt;FileSystem&gt; funkce
Tyto funkce v volné [ \<systému souborů >](../standard-library/filesystem.md) záhlaví provádět operace úpravy a dotaz na cesty, soubory, symbolických odkazů, adresářů a svazky. Další informace a příklady kódu najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).  
||||  
|-|-|-|  
|[absolutní](#absolute)|[začít](#begin)|[kanonickém tvaru](#canonical)|
|[kopírování](#copy)|[copy_file –](#copy_file)|[copy_symlink –](#copy_symlink)|
|[create_directories –](#create_directories)|[create_directory –](#create_directory)|[create_directory_symlink –](#create_directory_symlink)|
|[create_hard_link –](#create_hard_link)|[create_symlink –](#create_symlink)|[current_path](#current_path)|
|[end](#end)|[ekvivalentní](#equivalent)|[existuje](#exists)|
|[file_size –](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time –](#last_write_time)|[oprávnění](#permissions)|[read_symlink](#read_symlink)|
|[odebrat](#remove)|[remove_all –](#remove_all)|[Přejmenování](#rename)|
|[resize_file –](#resize_file)|[místo](#space)|[Stav](#status)|
|[status_known –](#status_known)|[swap](#swap)|[symlink_status –](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|  


## <a name=""></a>  <a name="absolute"></a>absolutní  
  
```  
path absolute(const path& pval, const path& base = current_path());
```  
  
 Vrátí absolutní cesta odpovídající funkce `pval` relativně k názvu cesty `base`:  
  
1.  Pokud pval.has_root_name() & & pval.has_root_directory() funkce vrátí pval.  
  
2.  Pokud pval.has_root_name() & &! pval.has_root_directory() funkce vrátí pval.root_name() / absolute(base).root_directory() / absolute(base).relative_path() / pval.relative_path().  
  
3.  Pokud! pval.has_root_name() & & pval.has_root_directory() funkce vrátí absolute(base).root_name() / pval.  
  
4.  Pokud! pval.has_root_name() & &! pval.has_root_directory() funkce vrátí absolute(base) / pval.  
  
## <a name="begin"></a>začít  
  
```  
const directory_iterator& begin(const directory_iterator& iter) noexcept;  
const recursive_directory_iterator& 
    begin(const recursive_directory_iterator& iter) noexcept;  
```  
  
 Obě funkce vrátí `iter`.  
  
## <a name="canonical"></a>kanonickém tvaru  
  
```  
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```  
  
 Všechny funkce představují absolutní cestu souboru pabs = absolutní (pval, základní) (nebo pabs = absolute(pval) pro přetížení se žádný základní parametr), pak snížit na kanonický tvar v tomto pořadí kroků:  
  
1.  Každých X komponent cesty pro které is_symlink(X) má hodnotu true je nahrazena read_symlink(X).  
  
2.  Každý komponent cesty. (tečka je to aktuální adresář vymezenému předchozí komponenty cesty) se odebere.  
  
3.  Každý pár komponenty cesty X nebo... (tečkami je nadřazený adresář vymezenému předchozí komponenty cesty) se odebere.  
  
 Funkce vrátí pabs.  
  
## <a name="copy"></a>kopírování  
  
```  
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;  
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;  
```  
  
 Funkce všechny pravděpodobně zkopírujte nebo odkaz na jeden nebo více souborů `from` k `to` pod kontrolou `opts`, který je považován za copy_options::none pro přetížení bez `opts` parametr. `opts`musí obsahovat maximálně jedno z:  
  
-   skip_existing, overwrite_existing nebo update_existing  
  
-   copy_symlinks nebo skip_symlinks  
  
-   directories_only, create_symlinks nebo create_hard_links  
  
 Funkce nejprve určit f hodnoty file_status pro `from` a t pro `to`:  
  
-   Pokud požádá & (copy_options::create_symlinks &#124; copy_options::skip_symlinks), voláním symlink_status –  
  
-   voláním stav, jinak hodnota  
  
-   Jinak se zobrazovat chyby.  
  
 Pokud! exists(f) &#124; &#124; ekvivalent (f, t) &#124; &#124; is_other(f) &#124; &#124; is_other(t) &#124; &#124; is_directory(f) & & is_regular_file(t), pak ohlaste chybu (a udělat nic jiného).  
  
 Jinak pokud is_symlink(f) pak:  
  
-   Pokud možnosti & copy_options::skip_symlinks udělejte nic.  
  
-   Jinak pokud! exists(t) & & Možnosti & copy_options::copy_symlinks pak copy_symlink – (z, požádá).  
  
-   Jinak se zobrazovat chyby.  
  
 Jinak pokud is_regular_file(f) pak:  
  
-   Pokud požádá & copy_options::directories_only pak nedělat nic.  
  
-   Jinak pokud požádá & copy_options::create_symlinks pak create_symlink(to, from).  
  
-   Jinak pokud požádá & copy_options::create_hard_links pak create_hard_link(to, from).  
  
-   Jinak pokud is_directory(f) pak copy_file – (z na/from.filename(), požádá).  
  
-   Copy_file –, jinak hodnota (od, požádá).  
  
 Jinak pokud is_directory(f) & & (výslovný & copy_options::recursive &#124; &#124;! požádá) pak:  
  
```cpp  
if (!exists(t))
{  // copy directory contents recursively  
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }

}
```  
  
 Nedělat nic, jinak hodnota.  
  
## <a name="opy_file"></a>copy_file –  
  
```  
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;  
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;  
```  
  
 Funkce všechny pravděpodobně zkopírovat soubor na `from` k `to` pod kontrolou `opts`, který je považován za copy_options::none pro přetížení bez `opts` parametr. `opts`musí obsahovat maximálně jeden skip_existing, overwrite_existing nebo update_existing.  
  
 Pokud existuje\(k\) && \!\(požádá & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options::update_existing\) \) poté sestavu jako chybu, která daný soubor již existuje.  
  
 Jinak Pokud \!existuje\(k\) &#124; &#124; požádá & copy_options::overwrite_existing &#124; &#124; požádá & copy_options::update_existing & & last_write_time –\(na \) \< last_write_time –\(z\) &#124; &#124; \! \(požádá & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options:update_existing\) \) pak pokus o zkopírování obsah a atributy souboru ze souboru. Sestavy jako chybu, pokud se nezdaří pokus o kopírování.  
  
 Funkce vrátí hodnotu PRAVDA, pokud dojde k pokusu o kopírování a úspěšné, jinak hodnota false.  
  
## <a name="copy_symlink "></a>copy_symlink –  
  
```  
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;  
```  
  
 Pokud is_directory\(z\) funkce volá create_directory_symlink –\(z možnosti\). Jinak zavolá create_symlink –\(z možnosti\).  
  
## <a name="create_directories"></a>create_directories –  
  
```  
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;  
```  
  
 Pro název cesty, jako\/b\/c funkce vytvoří adresáře a a a\/b podle potřeby tak, aby mohl vytvořit adresář\/b\/c podle potřeby. Vrátí hodnotu true pouze pokud ve skutečnosti vytvoří adresář `pval`.  
  
## <a name="create_directory"></a>create_directory –  
  
```  
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;  
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;  
```  
  
 Funkce vytvoří adresář `pval` podle potřeby. Vrátí hodnotu true pouze pokud ve skutečnosti vytvoří adresář `pval`, v takovém případě zkopíruje oprávnění z existující soubor `attr`, nebo využívá perms::all pro přetížení bez `attr` parametr.  
  
## <a name="create_directory_symlink "></a>create_directory_symlink –  
  
```  
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;  
```  
  
 Funkce vytvoří odkaz jako symlink do adresáře `to`.  
  
## <a name="create_hard_link"></a>create_hard_link –  
  
```  
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;  
```  
  
 Funkce vytvoří odkaz jako pevný odkaz na zadaný adresář nebo soubor `to`.  
  
## <a name="create_symlink "></a>create_symlink –  
  
```  
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;  
```  
  
 Vytvoří funkci `link` jako symlink do souboru `to`.  
  
## <a name="current_path"></a>current_path  
  
```  
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;  
```  
  
 Funkce s žádný parametr `pval` vrátí název cesty pro aktuální adresář. Zbývající funkce nastavit aktuální adresář `pval`.  
  
## <a name="end"></a>end  
  
```  
directory_iterator& end(const directory_iterator& iter) noexcept;  
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;  
```  
  
 Vrátí první funkce directory_iterator\( \) a druhý funkce vrátí hodnotu recursive_directory_iterator\(\)  
  
## <a name="equivalent"></a>ekvivalentní  
  
```  
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;  
```  
  
 Funkce vrátí hodnotu true pouze v případě `left` a `right` určit stejné entity systému souborů.  
  
## <a name="exists"></a>existuje  
  
```  
bool exists(file_status stat) noexcept;  
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce status_known – & & stat.type\( \) \! \= file_not_found. Druhý a třetí funkce vrátí existuje\(stav\(pval\)\).  
  
## <a name="file_size"></a>file_size –  
  
```  
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;  
```  
  
 Funkce vrátí velikost v bajtech soubor určený v `pval`, pokud existuje\(pval\) & & is_regular_file\(pval\) a velikost souboru se dá určit. V opačném případě budou sestavy k chybě a vraťte se uintmax_t\(\-1\).  
  
## <a name="hard_link_count"></a>hard_link_count  
  
```  
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;  
```  
  
 Funkce vrátí počet pevných odkazů pro `pval`, nebo \-1, pokud dojde k chybě.  
  
## <a name="hash_value"></a>hash_value  
  
```  
size_t hash_value(const path& pval) noexcept;  
```  
  
 Funkce vrátí hodnotu hash pro pval.native\(\).  
  
## <a name="is_block_file"></a>is_block_file  
  
```  
bool is_block_file(file_status stat) noexcept;  
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::block. Zbývající funkce vrátí is_block_file\(stav\(pval\)\).  
  
## <a name="is_character_file"></a>is_character_file  
  
```   
bool is_character_file(file_status stat) noexcept;  
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::character. Zbývající funkce vrátí is_character_file\(stav\(pval\)\).  
  
## <a name="is_directory "></a>is_directory  
  
```   
bool is_directory(file_status stat) noexcept;  
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::directory. Zbývající funkce vrátí is_directory_file\(stav\(pval\)\).  
  
## <a name="is_empty"></a>is_empty  
  
```   
bool is_empty(file_status stat) noexcept;  
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;  
```  
  
 Pokud is_directory\(pval\) pak funkce vrátí hodnotu directory_iterator\(pval\) \= \= directory_iterator\(\); jinak vrátí název_ velikost\(pval\) \= \= 0.  
  
## <a name="is_fifo"></a>is_fifo  
  
```  
bool is_fifo(file_status stat) noexcept;  
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::fifo. Zbývající funkce vrátí is_fifo\(stav\(pval\)\).  
  
## <a name="is_other"></a>is_other  
  
```  
bool is_other(file_status stat) noexcept;  
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::other. Zbývající funkce vrátí is_other\(stav\(pval\)\).  
  
## <a name="s_regular_file"></a>is_regular_file  
  
```   
bool is_regular_file(file_status stat) noexcept;  
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::regular. Zbývající funkce vrátí is_regular_file\(stav\(pval\)\).  
  
## <a name="is_socket"></a>is_socket  
  
```   
bool is_socket(file_status stat) noexcept;  
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::socket. Zbývající funkce vrátí is_socket\(stav\(pval\)\).  
  
## <a name="is_symlink"></a>is_symlink  
  
```   
bool is_symlink(file_status stat) noexcept;  
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí první funkce stat.type\( \) \= \= file_type::symlink. Zbývající funkce vrátí is_symlink\(stav\(pval\)\).  
  
## <a name="last_write_time"></a>last_write_time –  
  
```   
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;  
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;  
```  
  
 První dvě funkce vrátí čas poslední změny dat pro `pval`, nebo file_time_type\(\-1\) Pokud dojde k chybě. Poslední dvě funkce nastavit čas poslední změny dat pro `pval` k new_time.  
  
## <a name="permissions"></a>oprávnění  
  
```  
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;  
```  
  
 Nastavte oprávnění pro cesty určené, které funkce `pval` maska a perms::mask pod kontrolou oprávnění & \(perms::add_perms &#124; perms::remove_perms\). Maska musí obsahovat maximálně jeden perms::add_perms a perms::remove_perms.  
  
 Pokud maska & perms::add_perms funkce nastavte oprávnění stav\(pval\).permissions\( \) &#124; maska & perms::mask. Jinak, pokud maska & perms::remove_perms funkce nastaven na stav oprávnění\(pval\).permissions\( \) & ~\(maska & perms::mask\). Funkce, jinak nastavte oprávnění k maska & perms::mask.  
  
## <a name="read_symlink"></a>read_symlink  
  
```  
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```  
  
 Funkce sestav cesta k chybě a vraťte se\( \) Pokud \!is_symlink\(pval\). Jinak, funkce vrátí objekt typu `path` obsahující symbolický odkaz.  
  
## <a name="remove"></a>odebrat  
  
```  
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;  
```  
  
 Funkce vrátí hodnotu true, pouze pokud existuje\(symlink_status –\(pval\) \) a soubor se úspěšně odebral. Symlink se odebere, ne soubor, které určí.  
  
## <a name="remove_all"></a>remove_all –  
  
```  
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;  
```  
  
 Pokud `pval` je adresář, rekurzivní funkce odebrat všechny položky adresář a potom položku sám sebe. Funkce, jinak volání odebrat. Počet úspěšně odebral všechny elementy vracejí.  
  
## <a name="rename"></a>Přejmenování  
  
```  
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;  
```  
  
 Funkce přejmenovat `from` k `to`. Symlink je sám přejmenovat, ne soubor, které určí.  
  
## <a name="resize_file"></a>resize_file –  
  
```  
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;  
```  
  
 Změnit velikost souboru takové funkce této file_size –\(pval\) \= \= velikost  
  
## <a name="space"></a>místo  
  
```  
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;  
```  
  
 Vrátí informace o svazku určené, které funkce `pval`, do struktury typu `space_info`. Struktura obsahuje uintmax_t\(\-1\) pro jakoukoli hodnotu, která nelze určit.  
  
## <a name="status"></a>Stav  
  
```  
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;  
```  
  
 Funkce vrátí stav pathname, typ souboru a oprávnění, která je spojená s `pval`. Symlink je sám netestováno, ale soubor označí.  
  
## <a name="status_known"></a>status_known –  
  
```  
bool status_known(file_status stat) noexcept;  
```  
  
 Funkce vrátí hodnotu stat.type\( \) \! \= file_type::none  
  
## <a name="swap"></a>swap  
  
```  
void swap(path& left, path& right) noexcept;  
```  
  
 Funkce výměny obsah `left` a `right`.  
  
## <a name="symlink_status"></a>symlink_status –  
  
```  
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;  
```  
  
 Funkce vrátí stav symlink pathname, typ souboru a oprávnění, která je spojená s `pval`. Funkce chovají stejně jako stav\(pval\) s tím rozdílem, že symlink je sám testovat, ne soubor jmenuje.  
  
## <a name="system_complete"></a>system_complete  
  
```  
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```  
  
 Funkce vrátí absolutní cestu souboru, který bere v úvahu, podle potřeby, aktuální adresář přidružený jeho název kořenového adresáře. \(Pro Posix, vrátí funkce absolutní\(pval\).\)  
  
## <a name="temp_directory_path"></a>temp_directory_path  
  
```  
path temp_directory_path();
path temp_directory_path(error_code& ec);
```  
  
 Funkce vrátí název cesty k adresáři vhodný pro dočasné soubory.  
  
## <a name="u8path"></a>u8path  
  
```  
template <class Source>  
path u8path(const Source& source);

template <class InIt>  
path u8path(InIt first, InIt last);
```  
  
 První funkce se chová stejně jako path(source) a druhý funkce se chová stejně jako cestu (první, poslední) s tím rozdílem, že určený zdroj v každém případě je považován za pořadí elementů char kódovaná jako UTF-8, bez ohledu na to systém souborů.

