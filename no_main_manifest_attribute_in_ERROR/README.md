# no main manifest attribute in 에러

## https://dongjuppp.tistory.com/87

이 블로그가 아주 잘 설명을 해주고 있다.
그치만 나는 이방법들로 해결하지 못했다.... (나중에 이분꺼를 정리해야겠다.)

이유는 pom.xml 을 이상하게 작성했기 때문이다. 

`<plugins>` 과 `<pluginManagement/>`을 같이 썼다.

생각해보니 `<pluginManagement/>` 을 써서 못찾은건가 ??
한번 테스트를 해보고 글을 수정해야겠다.

중간에 삽질한 코드를 올려야 다음에 이해가 잘 될려나 ? 모르겠다. 다음에 삽질코드와 저 블로그의 글을 정리해야겠다.

고친 후 내 pom.xml

    ...
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                    <annotationProcessorPaths>
                        <path>
                            <groupId>org.mapstruct</groupId>
                            <artifactId>mapstruct-processor</artifactId>
                            <version>${org.mapstruct.version}</version>
                        </path>
                        <path>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                            <version>${org.projectlombok.version}</version>
                        </path>
                        <path>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok-mapstruct-binding</artifactId>
                            <version>${lombok-mapstruct-binding.version}</version>
                        </path>
                    </annotationProcessorPaths>

                </configuration>
            </plugin>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
