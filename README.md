# Asyncschwab
> **Note:** This project is a work in progress. Features and documentation may change as development continues.

> **Request for Help:** Contributions, suggestions, and feedback are welcome! If you'd like to help improve Asyncschwab, please open an issue or submit a pull request.

> **Status Update:** As of now, the `main` branch is fully functional.
>
> **How It Works:** The tokens file operations remain fully blocking for simplicity and reliability, while only the API calls made through the `Client` class are asynchronous.

Asyncschwab is an asynchronous rewrite of the original [schwabdev](https://github.com/tylerebowers/Schwabdev) repository. This project aims to improve performance and scalability by leveraging Python's `async` and `await` features.

## Features

- Fully async API calls
- Improved concurrency handling
- Modern Python async patterns

## Example

```python
import asyncio
from asyncschwab import Client

async def main():
    tickers = ["AAPL", "MSFT", "GOOGL"]
    
    async with Client(os.getenv("app_key"), os.getenv("app_secret"), os.getenv("callback_url")) as client:
        async with asyncio.TaskGroup() as tg:
            results = [tg.create_task(client.price_history(
                i,
                periodType="day",
                period=1,
                frequencyType="minute",
                frequency=5,
                needExtendedHoursData="False",
                startDate=datetime(2025, 5, 5),
                endDate=datetime(2025, 5, 6),
            )) for i in tickers]

        print([await result for result in results])

asyncio.run(main())
```

> **Note:** For compatibility with `aiohttp`, boolean values in API parameters (such as `needExtendedHoursData`) must be passed as strings (`"True"` or `"False"`), not as Python `bool` types.  
> For more details, see [Why isn't boolean supported by the URL query API?](https://github.com/aio-libs/yarl#why-isnt-boolean-supported-by-the-url-query-api).

### MIT License

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.