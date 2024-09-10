Java records are pretty much like classes, but they're used as a way to transfer data between different layers of an application while offering a concise and more readable way to do so.

When creating a Data Transfer Object (DTO) in a Java application using a plain java class, you'd end up with something like this:

```java
public class DoctorDTO {
    private String name;
    private String code;
    private String specialty;

    public DoctorDTO(String name, String code, String specialty) {
        this.name = name;
        this.code = code;
        this.specialty = specialty;
    }

    public String getName() {
        return name;
    }

    public String getCode() {
        return code;
    }

    public String getSpecialty() {
        return specialty;
    }
}
```

While it could be simplified to this using a record:

```java
record DoctorRecord(String name, String code, String specialty) {}
```

It basically helps keeping your code less verbose and also offer **immutability,** which is good for data transfer security reasons.