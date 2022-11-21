05-04-2022
16:53
Authors: Khutuev Tamerlan.
***
Tags: #nestjs #redis
***
# Подключение Redis
Подключение на примере маленького модуля кеширования постов в приложении. 
```typescript
import { Injectable } from '@nestjs/common';
import { createClient } from 'redis'; 


@Injectable()

export class RedisCacheService {

	private readonly client = createClient(); //если оставить пустой то подключается к дефолтному порту на localhost
	//для подключеня к другому ip необходимо добавить {url: 'redis:ip'}

	async setAllPosts(posts: string): Promise<void> {
		await this.set('posts', posts, 5);
	}

	async getAllPosts(): Promise<string | null> {
		const posts = await this.get('posts');
		if (posts === 'nil') {
			return null;
		}
		return posts;
	}

	private async set(
		key: string,
		value: string,
		ttl_sec: number,
		): Promise<void> {
		await this.client.connect(); //подключение
		this.client.set(key, value, { //добавления значения
			EX: ttl_sec,
			NX: true,
		});
	this.client.quit(); //завершить подключение
}

  

	private async get(key: string): Promise<string> {
		await this.client.connect();
		const data: string = await this.client.get(key); 
		this.client.quit();
		return data;
	}
}
```


