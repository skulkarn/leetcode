Serialize and deserialize a map

// Dict(“a”: StringWrapper(“apple”), “b”: Dict(“b”: “blueberry”, “c”: “cranberry”))
// “{a:apple,b:{b:blueberry,c:cranberry}}”
DictEntry.java:

public interface DictEntry {
public boolean isDict();
}

Dict.java:

public class Dict implements DictEntry {
private Map<String, DictEntry> map;

public Dict(Map<String, DictEntry> map) {
this.map = map;
}

public boolean isDict() {
return true;
}

public Set getKeys() {
return map.keySet();
}

public DictEntry get(String key) {
return map.get(key);
}
}

StringWrapper.java:

public class StringWrapper implements DictEntry {

private String str;

public StringWrapper(String str) {
this.str = str;
}

public boolean isDict() {
return false;
}

public String getValue() {
return str;
}
}