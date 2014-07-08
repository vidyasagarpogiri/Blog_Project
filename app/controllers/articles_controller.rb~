class ArticlesController < ApplicationController
  http_basic_authenticate_with name: "admin", password: "admin", except: [:index, :show]
 
  def index
    @articles = Article.all
  end
  
  def show
  #raise params.inspect
    @article = Article.find(params[:id])
  end
  
  def new
   @article = Article.new
   end
   
  def edit
    @article = Article.find(params[:id])
  end
   
  def create
   @article = Article.new(params.require(:article).permit(:title, :description, :category, :tags))
   @article.save
   redirect_to @article
  end
   
   def update
  @article = Article.find(params[:id])
 
  if @article.update(article_params)
    redirect_to @article
  else
    render 'edit'
  end
  end

  def destroy
  @article = Article.find(params[:id])
  @article.destroy
 
  redirect_to articles_path
  end

   
  private
  def article_params
    params.require(:article).permit(:title, :description, :category, :tags)
  end
end
