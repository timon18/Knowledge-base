21-03-2023
21:11
Authors: Tamerlan Khutuev
***
Tags: #stub #spring
***
# SecurityConfig

Для того, что бы настроить security необходимо написать класс-конфигурацию в которой будет создаваться бин SecurityFilterChain. 

```java
@Configuration  
@EnableWebSecurity  
public class SecurityConfig {
	@Bean  
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
	}
}
```

Пример настроенного:

```java
@Configuration  
@EnableWebSecurity  
public class SecurityConfig {  
    private final JwtTokenProvider jwtTokenProvider;  
    private static final String LOGIN_ENDPOINT = "/login";  
    private static final String REGISTER_ENDPOINT = "/register";  
  
    @Autowired  
    public SecurityConfig(JwtTokenProvider jwtTokenProvider) {  
        this.jwtTokenProvider = jwtTokenProvider;  
    }  
  
    @Bean  
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {  
        http  
                .httpBasic().disable()  
                .csrf().disable()  
                .sessionManagement()
				.sessionCreationPolicy(SessionCreationPolicy.STATELESS)  
                .and()  
                .authorizeRequests()  
                .requestMatchers(OPTIONS).permitAll()  
                .requestMatchers(  
                        LOGIN_ENDPOINT,  
                        REGISTER_ENDPOINT,  
                        "/csrf",  
                        "/static/**",  
                        "/swagger-ui.html",  
                        "/swagger-ui/**",  
                        "/v3/api-docs/**"  
                ).permitAll()  
                .anyRequest().authenticated()  
                .and()  
                .apply(new JwtConfigurer(jwtTokenProvider)); //Добавляем свой фильтр
        return http.build();  
    }  
}
```