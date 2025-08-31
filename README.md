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

### MIT License

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.