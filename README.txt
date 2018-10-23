1.  add response cache attribute to method   get methods only

2.  add nuget package:  Microsoft.AspNetCore.ResponseCaching

3.  add middle where into configure and configureservices methods
   public void ConfigureServices(IServiceCollection services)
        {
            // cache middleware
            services.AddResponseCaching();

            services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

            
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }
            else
            {
                app.UseHsts();
            }

            // Cache Middleware
            app.UseResponseCaching();

            app.UseHttpsRedirection();
            app.UseMvc();
        }





URLs:
https://docs.microsoft.com/en-us/aspnet/core/performance/caching/response?view=aspnetcore-2.1
https://docs.microsoft.com/en-us/aspnet/core/performance/caching/middleware?view=aspnetcore-2.1

https://docs.microsoft.com/en-us/aspnet/core/mvc/views/tag-helpers/built-in/distributed-cache-tag-helper?view=aspnetcore-2.1
https://docs.microsoft.com/en-us/aspnet/core/mvc/views/tag-helpers/built-in/cache-tag-helper?view=aspnetcore-2.1

